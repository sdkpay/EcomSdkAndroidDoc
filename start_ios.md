# [EcomSdkAndroidDocs](https://sdkpay.github.io/EcomSdkAndroidDocs)

##### [Начало работы](https://sdkpay.github.io/EcomSdkAndroidDocs/start) | [Сценарий оплаты](https://sdkpay.github.io/EcomSdkAndroidDocs/payment_script) | [Работа в режиме песочницы](https://sdkpay.github.io/EcomSdkAndroidDocs/sandbox_mode) | [Вспомогательные структуры данных](https://sdkpay.github.io/EcomSdkAndroidDocs/data_structures) | [Актуальная версия SDK](https://sdkpay.github.io/EcomSdkAndroidDocs/version)
---
## Платформа для интеграции SDK
###### [Android](https://sdkpay.github.io/EcomSdkAndroidDocs/start_android) | [IOS](https://sdkpay.github.io/EcomSdkAndroidDocs/start_ios) | [Flutter](https://sdkpay.github.io/EcomSdkAndroidDocs/start_flutter) | [React-Native](https://sdkpay.github.io/EcomSdkAndroidDocs/start_react-native)
---

# Начало работы для iOS
> Xcode 14+
> Версия iOS 14.0 и выше

## Подключение SDK к проекту

### Настройка info.plist
Для корректной работы SDK в файле info.plist приложения должны быть добавлены следующие параметры
```
<key>NSAppTransportSecurity</key>
      <dict>
         <key>NSExceptionDomains</key>
         <dict>
            <key>gate1.spaymentsplus.ru</key>
            <dict>
               <key>NSExceptionAllowsInsecureHTTPLoads</key>
               <true/>
            </dict>
         </dict>
      </dict>
    <key>NSLocationWhenInUseUsageDescription</key>
    <string>Данные о местонахождении собираются и отправляются на сервер для безопасного проведения оплаты</string>
```
> NSLocationWhenInUseUsageDescription - Если у вас уже используется этот параметр, то дублировать его не нужно

### SPM
```
dependencies: [
    .package(url: "https://github.com/sdkpay/EcomSdkPackage", .upToNextMajor(from: "0.5.0"))
]
```

### Бинарный артефакт
Подключить SDK для успешной работы также можно с помощью [бинарного артефакта](https://github.com/sdkpay/EcomSdkPackage). Перетащите скачанный файл **EcomSdk.xcframework** в `Frameworks, Libraries, and Embedded Content`, а также выставите у зависимости параметр `Embed & Sign`
