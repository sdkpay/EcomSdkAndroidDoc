# [EcomSdkAndroidDoc](https://sdkpay.github.io/EcomSdkAndroidDoc)

#### [Регистрация заказов в платежном шлюзе Сбера](https://sdkpay.github.io/EcomSdkAndroidDoc/order_registration) | [Начало работы](https://sdkpay.github.io/EcomSdkAndroidDoc/start) | [Сценарий оплаты](https://sdkpay.github.io/EcomSdkAndroidDoc/payment_script) | [Работа в режиме песочницы](https://sdkpay.github.io/EcomSdkAndroidDoc/sandbox_mode) | [Вспомогательные структуры данных](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures) | [Актуальная версия SDK](https://sdkpay.github.io/EcomSdkAndroidDoc/version) | [Поддержка](https://sdkpay.github.io/EcomSdkAndroidDoc/support)

<br>

# Вспомогательные структуры данных

## EcomSdkSetupConfig

#### Конфиг для инициализации SDK

|Параметр|Тип|Дефолтное значение| Обязательный | Описание                                                                                                                                                                                  |
|---|:---:|:---:|:------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|context|Context|-|      Да      | Context или ApplicationContext приложения                                                                                                                                                 |
|ecomUiPreferences|EcomUiPreferences|-|     нет      | Настройки для уникализации интерфейса EcomUiPreferences.<br> [EcomUiPreferences](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#ecomUiPreferences)                            |                                                                                                                                                             |
|stage|EcomSdkStage|-|      Да      | Список стендов для работы с EcomSdk.<br>Структура [EcomSdkStage](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#ecomsdkstage)                                                 |
|disabledFeatures|List\<EcomSdkFeature\>|listOf()|     Нет      | Список выключенных features.<br>Структура [EcomSdkFeature](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#ecomsdkfeature)                                                     |
|enableLogging|Boolean|false|     Нет      | Флаг включенного логирования для партнера                                                                                                                                                 |
|callback|(Boolean) -> Unit|-|      Да      | Блок, отрабатыващий после настройки SDK. Корректное значение колбэка true                                                                                                                 |
|metricCallback|(Pair<AnalyticalEvent, Int>) -> Unit|null|     Нет      | Блок, отбрасывающий аналитические бизнес метрики при прохождении сценария SDK.<br>Структура [AnalyticalEvent](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#analyticalevent) |

<br>

## EcomUiPreferences

#### Параметры кастомизации UI EcomSdk

```
/**
 * Параметры кастомизации EcomSdk
 */
data class EcomUiPreferences(
    /**
     * Настройки светлой темы 
    /*
    val lightTheme: EcomUIColorPreferences? = null,
    /**
     * Настройки темной темы
     */
    val darkTheme: EcomUIColorPreferences? = null,
    /**
     * Общие настройки
     */
    val common: EcomUICommonPreferences? = null
)
```

Структура [EcomUIColorPreferences](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#ecomUIColorPreferences)
Структура [EcomUICommonPreferences](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#ecomUICommonPreferences)

<br>

## EcomUIColorPreferences

#### Параметры кастомизации цветовой схемы UI EcomSdk

```
/**
 * Настройки цветов
 */
class EcomUIColorPreferences(
    /**
     * Цвет поля ввода в формате RGB (#FFFFFF)
     */
     inputBG: String? = null,
        
    /**
     * Цвет основного бэкграунда в формате RGB (#FFFFFF)
     */
    mainBG: String? = null,
      
    /**
     * Основной цвет текста в формате RGB (#FFFFFF)
     */
     textPrimary: String? = null,

    /**
     * Вторичный цвет текста в формате RGB (#FFFFFF)
     */
    textSecondary: String? = null,

    /**
     * Цвет успешного выполнения в формате RGB (#FFFFFF)
     */
    accentSuccess: String? = null,

    /**
     * Цвет ошибки в формате RGB (#FFFFFF)
     */
    accentError: String? = null,

    /**
     * Цвет для анимации загрузки в формате RGB (#FFFFFF)
     */
    loader: String? = null,

    /**
     * Цвет для вторичных кнопок в формате RGB (#FFFFFF)
     */
    buttonSecondary: String? = null,

    /**
     * Ссылка на иконка мерчанта (URL)
     */
    merchantIcon: String? = null,
)
```

<br>

## EcomUICommonPreferences

#### Общие параметры кастомизации UI EcomSdk

```
/**
 * Общие настройки UI EcomSdk
 */
data class EcomUICommonPreferences(
    /**
     * Размер радиуса углов элементов
     */
    val radiusSize: SBRadiusSize? = SBRadiusSize.M,
    
    /**
     * Размер текста
     */
    val textSize: SBTextSize? = SBTextSize.M,
)
```

Структура [SBRadiusSize](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#sbRadiusSize)
Структура [SBTextSize](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#sbTextSize)

<br>

## SBRadiusSize

#### Радиус для элементов UI EcomSdk

```
/**
 * Размер радиуса углов элементов
 */
enum class SBRadiusSize(val value: String) {
    S("s"),
    M("m"),
    L("l"),
}
```

## SBTextSize

#### Радиус для элементов UI EcomSdk

```
/**
 * Размер текста
 */
enum class SBTextSize(val value: String) {
    S("s"),
    M("m"),
    L("l"),
}
```

<br>

## EcomSdkStage

#### Стенды SDK

```
/**
 * Enum со стендами SDK
 * */
public enum class EcomSdkStage: Stage {
    /** Продовый стенд */
    Prod,
    /** Песочница */
    SandBox
}
```

<br>

## EcomSdkFeature

#### Фичи SDK

```
/**
 * Enum с фичами SDK
 * */
enum class EcomSdkFeature {
    /** Отображение результирующих экранов */
    RESULT_VIEW,
    /** Приём платежей через СБП */
    PAY_BY_SBP,
    /** Приём платежей через SPaySDK */
    PAY_BY_SPAY,
    /** Прием платежей картами */
    BINDING,
    /** Оплата новой картой */
    NEW_CARD
}
```

<br>

## EcomSdkMerchantOptionsConfig

#### Конфиг для запуска сценария оплаты методом `pay`

|Параметр|Тип|Дефолтное значение| Обязательный | Описание                                                                                                                                                                                                 |
|---|:---:|:---:|:------------:|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|context|Context|-|      Да      | ActivityContext приложения                                                                                                                                                                               |
|bankInvoiceId|String|-|      Да      | Уникальный идентификатор заказа в Платежном шлюзе Банка. Необходимо передавать значение sbolBankInvoiceId из ответа на Запрос регистрации заказа                                                         |
|apiKey|String|-|      Да      | Ключ для работы с сервисами платежного шлюза через SDK                                                                                                                                                   |
|merchantLogin|String|-|      Да      | Логин для работы с сервисами платежного шлюза                                                                                                                                                            |
|orderNumber|String|-|      Да      | Уникальный идентификатор заказа в системе Партнера                                                                                                                                                       |
|appPackageName|String|-|      Да      | Package (BuildConfig.APPLICATION_ID) приложения, по которому необходимо вернуть Плательщика в приложение Партнера, после аутентификации в СберБанк Онлайн                                                |
|preferredSPayMethod|EcomSPayMethod|-|     Нет      | Предпочитаемый метод для оплаты через SPaySdk<br>Структура [EcomSPayMethod](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#ecomSPayMethod)                                                   |                                                                                                                                                            |
|callback|(EcomSdkResult) -> Unit|-|      Да      | Блок, отрабатыващий после завершения сценария оплаты Плательщиком, возвращающий результат оплаты.<br>Структура [EcomSdkResult](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#ecomsdkresult) |

<br>

## EcomSPayMethod

#### Доступные способы оплаты через SPaySdk

```
sealed interface EcomSPayMethod : Parcelable {
    /**
     * Оплата с использованием 6-ти частей и обычной оплатой (без paymentToken и paymentOrder)
     */
    object Default : EcomSPayMethod
    
    /**
     * Оплата с параметрами для проведения оплаты (с paymentToken и paymentOrder)
     */
    object WithBankInvoiceId : EcomSPayMethod
    
    /**
     * Оплата со списанием бонусов Спасибо
     */
    object WithBonuses : EcomSPayMethod
    
    /**
     * Оплата без рефреша с использованием 6-ти частей и обычной оплатой (без paymentToken и paymentOrder)
     */
    object WithoutRefresh : EcomSPayMethod
    
    /**
     * Оплата с использованием платежного счета  
     */
    object WithPaymentAccount: EcomSPayMethod
    
    /**
     * Оплата с использованием платежа на 6 частей
     */
    object WithPartPay: EcomSPayMethod

    /**
     * Оплата по связке
     *
     * @param bindingId Уникальный идентификатор связки
     */
    data class WithBinding(val bindingId: String): EcomSPayMethod

    /**
     * Оплата с авторизацией только по номеру телефона
     *
     * @param phoneNumber Номер телефона
     */
    data class WithPhoneNumber(val phoneNumber: String): EcomSPayMethod
}
```

<br>

## EcomSdkResult

#### Результат выполнения метода `pay`

```
/**
     * Возможные результаты проведения оплаты
     *
     * @property Success оплата произведена успешно
     * @property Waiting статус оплаты неизвестен
     * @property Cancel оплата отменена пользователем
     * @property Error оплата не была выполнена из-за ошибки
     *
     * @param localSessionId уникальный номер сессии оплаты через SDK
     */
    sealed class EcomSdkResult(open var localSessionId: String? = null) {
        data class Success(override var localSessionId: String? = null) : EcomSdkResult(localSessionId)

        /**
         * Класс неизвестного статуса оплаты при работе с EcomSdk
         *
         * @param httpCode код ответа http
         * @param errorCode внутренний код ответа от севера
         * @param description описание ошибки
         * @param bankInvoiceId уникальный номер заказа в системе банка
         * @param localSessionId уникальный номер сессии оплаты через SDK
         */
        data class Waiting(
            val httpCode: String? = null,
            val errorCode: String? = null,
            val description: String? = null,
            val bankInvoiceId: String? = null,
            override var localSessionId: String? = null,
        ) : EcomSdkResult(localSessionId)

        data class Cancel(override var localSessionId: String? = null) : EcomSdkResult(localSessionId)

        /**
         * Класс ошибки при работе с EcomSdk
         *
         * @param httpCode код ответа http
         * @param errorCode внутренний код ответа от севера
         * @param description описание ошибки
         * @param bankInvoiceId уникальный номер заказа в системе банка
         * @param localSessionId уникальный номер сессии оплаты через SDK
         */
        data class Error(
            val httpCode: String? = null,
            val errorCode: String? = null,
            val description: String? = null,
            val bankInvoiceId: String? = null,
            override var localSessionId: String? = null,
        ) : EcomSdkResult(localSessionId)
    } 
```

<br>

## AnalyticalEvent

#### Структура бизнес метрик для партнера
```
/**
 * Класс данных, описывающий отправляемые события в аналитику, для партнера
 *
 * @param action аналитическое событие
 * @param httpCode код запроса https
 * @param errorCode внутренний код ошибки
 * @param description описание ошибки
 */
data class AnalyticalEvent(
    val action: String,
    val httpCode: Int? = null,
    val errorCode: String? = null,
    val description: String? = null,
)
```

<br>

## Платежные инструменты для работы в режиме песочницы

| Тип тестирования | Номер карты | Срок действия карты | CVV |  SMS-код | Пароль |
| --- |:---:|:---:|:---:|:---:|:---:|
| Без 3ds | 4279380620378929 | 06/26 | 353 | нет | нет |
| С 3ds | 2202208020207685 | 05/27 | 133 | 111111 | нет |
| С 3ds | 2201382000000047 | 05/27 | 133 | нет | 1qwezxc |
