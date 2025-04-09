# [EcomSdkAndroidDoc](https://sdkpay.github.io/EcomSdkAndroidDoc)

#### [Регистрация заказов в платежном шлюзе Сбера](https://sdkpay.github.io/EcomSdkAndroidDoc/order_registration) | [Начало работы](https://sdkpay.github.io/EcomSdkAndroidDoc/start) | [Сценарий оплаты](https://sdkpay.github.io/EcomSdkAndroidDoc/payment_script) | [Работа в режиме песочницы](https://sdkpay.github.io/EcomSdkAndroidDoc/sandbox_mode) | [Вспомогательные структуры данных](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures) | [Актуальная версия SDK](https://sdkpay.github.io/EcomSdkAndroidDoc/version) | [Поддержка](https://sdkpay.github.io/EcomSdkAndroidDoc/support)

<br>

# Работа в режиме песочницы

Песочница - режим работы SDK, который необходим для отладки процесса оплаты. В этом режиме есть возможность пройти весь процесс оплаты через SDK в приложении без регистрации реальных заказов. Это можно реализовать двумя способами. Рассмотрите первый простой вариант, он подойдет для тех, кто не интегрирован с платежным шлюзом Банка и ищет способ протестировать визуальную составляющую продукта. Реализуете сценарий «Оплата вне SDK». Если вы интегрированы с платежным шлюзом Сбера, то мы рекомендуем второй вариант - использовать идентификаторы заказов в Платежном шлюзе Банка из тестового окружения. Обратите внимание, что в зависимости от того, с какой именно версией протокола вы интегрированы могут потребоваться отдельные учетные данные для регистрации заказов

> В данном режиме не отображаются настоящие данные клиента

<br>

## Необходимые данные для тестирования

Для получения доступа к песочнице необходимо отправить запрос на почту *support@ecom.sberbank.ru*. В теме письма обязательно указать "Получение доступа к песочнице Sandbox SDK Ecom In-App".  
Также предоставляются [инструменты для тестирования](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#%D0%BF%D0%BB%D0%B0%D1%82%D0%B5%D0%B6%D0%BD%D1%8B%D0%B5-%D0%B8%D0%BD%D1%81%D1%82%D1%80%D1%83%D0%BC%D0%B5%D0%BD%D1%82%D1%8B-%D0%B4%D0%BB%D1%8F-%D1%80%D0%B0%D0%B1%D0%BE%D1%82%D1%8B-%D0%B2-%D1%80%D0%B5%D0%B6%D0%B8%D0%BC%D0%B5-%D0%BF%D0%B5%D1%81%D0%BE%D1%87%D0%BD%D0%B8%D1%86%D1%8B)

<br>

## Реализация в коде

В объект класса [EcomSdkSetupConfig](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#ecomsdksetupconfig) передайте в параметр *stage* значение **EcomSdkStage.SandBox**

### Kotlin

```
import modern.payments.ecomAndroid.EcomSdk
import modern.payments.ecomAndroid.api.EcomSdkSetupConfig
import modern.payments.ecomAndroid.api.EcomSdkStage

val config = EcomSdkSetupConfig(
    context = context,
    stage = EcomSdkStage.SandBox,
    disabledFeatures = listOf(),
    enableLoggingByMerchant = true,
    callback = { isSetupSucceed ->
    }
)

EcomSdk.getInstance().setup(config)
```

### Java

```
import modern.payments.ecomAndroid.EcomSdk;
import modern.payments.ecomAndroid.api.EcomSdkSetupConfig;
import modern.payments.ecomAndroid.api.EcomSdkStage; 

EcomSdkSetupConfig ecomSdkSetupConfig = new EcomSdkSetupConfig(
    getBaseContext(),
    EcomSdkStage.SandBox,
    new ArrayList<>(),
    true,
    result -> {
        if (result) {
            //do somethingOnSuccess
        } else {
            //do somethingOnFail
        }
        return null;
    }
);

EcomSdk.Companion.getInstance().setup(ecomSdkSetupConfig);
```
