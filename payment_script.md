# [EcomSdkAndroidDoc](https://sdkpay.github.io/EcomSdkAndroidDoc)

##### [Начало работы](https://sdkpay.github.io/EcomSdkAndroidDoc/start) | [Сценарий оплаты](https://sdkpay.github.io/EcomSdkAndroidDoc/payment_script) | [Работа в режиме песочницы](https://sdkpay.github.io/EcomSdkAndroidDoc/sandbox_mode) | [Вспомогательные структуры данных](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures) | [Актуальная версия SDK](https://sdkpay.github.io/EcomSdkAndroidDoc/version)
---

# Сценарий оплаты

Для запуска сценария оплаты SDK необходимо вызвать метод `pay` и передать в него **[EcomSdkMerchantOptionsConfig](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#ecomsdkmerchantoptionsconfig)**

> Обязательно корректно укажите значение параметра *appPackageName*. В противном случае при возврате из сбола после оплаты, если будет допущена ошибка в схеме, поднимется шторка с вариантами приложений для продолжения оплаты. Таким образом, сценарий разорвется.

### Kotlin
```
import modern.payments.ecomAndroid.EcomSdk
import modern.payments.ecomAndroid.api.EcomSdkMerchantOptionsConfig

val config = EcomSdkMerchantOptionsConfig(
    context = context,
    bankInvoiceId = BANK_INVOICE_ID,
    apiKey = API_KEY,
    merchantLogin = CLIENT_NAME,
    orderNumber = ORDER_NUMBER,
    appPackageName = APP_PACKAGE,
) { ecomSdkResult ->
    when (ecomSdkResult) {
        is EcomSdkResult.Success -> {
            //do something on success
            doOnSuccess()   
        }
        is EcomSdkResult.Error -> {
            //do something on error
            doOnError(ecomSdkResult.merchantError)
        }
        is EcomSdkResult.Waiting -> {
            //do something on waiting
            doOnWaiting();
        }
        is EcomSdkResult.Cancel -> {
            //do something on cancel
            doOnCancel();
        }
    }
}

EcomSdkApp.getInstance().pay(config)
```

### Java
```
import modern.payments.ecomAndroid.EcomSdk;
import modern.payments.ecomAndroid.api.EcomSdkMerchantOptionsConfig;
import modern.payments.ecomAndroid.api.EcomSdkMerchantOptionsConfig.*;

EcomSdkMerchantOptionsConfig ecomSdkMerchantOptionsConfig =
    new EcomSdkMerchantOptionsConfig(
        getBaseContext(),
        BANK_INVOICE_ID,
        API_KEY,
        MERCHANT_LOGIN,
        ORDER_NUMBER,
        PACKAGE_NAME,
        result -> {
            if (result instanceof EcomSdkResult.Success) {
            //do somethingOnSuccess
            } else if (result instanceof EcomSdkResult.Cancel) {
            //do somethingOnCancel
            } else if (result instanceof EcomSdkResult.Waiting) {
            //do somethingOnWaiting
            } else if (result instanceof EcomSdkResult.Error) {
            //do somethingOnError
            }
        return null;
        }
    );

EcomSdk.Companion.getInstance().pay(ecomSdkMerchantOptionsConfig);
```
