# Отчет о тестировании программы "Credit Card Number Validation" #
## Проверка работы программы валидации кредитных карт ##
4.06.2020 было проведено несколько видов тестирования программы валидации номеров кредитных карт. 
Такие как: нефункциональное тестирование (проверяли как хорошо программа выполняет свою функцию), тестирование установки (проверяли установку IntelliJ IDEA Community на Windows 10 и его запуск, работает ли приложение согласно инструкции, запускает ли оно код). Все виды тестирования проводились методом белого ящика, так как код программы был доступен.

На тестирование затрачено: 2 часа.

В результате тестирования выявлены следующие дефекты:

* https://github.com/Lebedeva-Kris/CC-Validator/issues/1

## Описание процесса тестирования ##
В процессе тестирования использовались следующие артефакты:

* краткий тест-план (была предоставлена информация о том какие карты нужно проверить, было предположено какие итоги будут в результате проверки, а так же было доступно руководство установки приложения и сам код);
* оформление баг-репортов (ссылки выше);
* составление самого отчета о тестировании.

В качестве тестовых данных использовались данные https://www.freeformatter.com/credit-card-number-generator-validator.html

* VISA 4024007114667958: ОК
* MasterCard 5528776724665085: ОК
* American Express (AMEX) 349825795544840: ОК
* Discover 6011614913711679: ОК
* JCB 3540588463314158: ОК
* Diners Club - North America 5455548305572361: ОК
* Diners Club - Carte Blanche 30339739311682: ОК
* Diners Club - International 36053794954476: ОК
* Maestro 6761906514706419: ОК
* Visa Electron 4175006486174384: ОК
* InstaPayment 6396417728526224: ОК

А также код, который был доступен: 
```
public class Main {
  public static void main(String[] args) {
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    String number = "5351719427810741";
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
  }

  public static boolean isValidCardNumber(String number) {
    if (number == null) {
      return false;
    }

    if (number.length() != 16) {
      return false;
    }

    long result = 0;
    for (int i = 0; i < number.length(); i++) {
      int digit;
      try {
        digit = Integer.parseInt(number.charAt(i) + "");
      } catch (NumberFormatException e) {
        return false;
      }

      if (i % 2 == 0) {
        digit *= 2;
        if (digit > 9) {
          digit -= 9;
        }
      }
      result += digit;
    }

    return (result != 0) && (result % 10 == 0);
  }
}
```

Тестирование производилось в следующем окружении:

* Windows 10
* InteliJ IDEA 2020.1.2

@coursar