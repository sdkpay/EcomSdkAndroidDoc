# [EcomSdkAndroidDoc](https://sdkpay.github.io/EcomSdkAndroidDoc)

##### [Начало работы](https://sdkpay.github.io/EcomSdkAndroidDoc/start) | [Сценарий оплаты](https://sdkpay.github.io/EcomSdkAndroidDoc/payment_script) | [Работа в режиме песочницы](https://sdkpay.github.io/EcomSdkAndroidDoc/sandbox_mode) | [Вспомогательные структуры данных](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures) | [Актуальная версия SDK](https://sdkpay.github.io/EcomSdkAndroidDoc/version)
---

<br>

# Начало работы

> Минимальная версия SDK - API 24

<br>

## Подключение SDK к проекту

Подключите SDK одним из удобных Вам способов: [Maven](https://sdkpay.github.io/EcomSdkAndroidDoc/start#maven) / [Aar](https://sdkpay.github.io/EcomSdkAndroidDoc/start#aar)

### Maven

Для получения зависимости из maven репозитория необходимо добавить его в **settings.gradle** файл вашего приложения
```
dependencyResolutionManagement {
    ...
    repositories {
        google()
        mavenCentral()
        ...
     ⁣   maven {
            ⁣name = "GitHubPackages"
            url = uri("https://maven.pkg.github.com/sdkpay/EcomAndroidSdkPackages")
                
        }
    }
}
```
Далее нужно перейти в **build.gradle** вашего модуля и добавить зависимости внутрь блока `dependencies`
```
dependencies {
    ...
    implementation("ru.spaymentsplus.libraries:ecomsdk:$version")
    ...
}
```

### AAR

Пакет дистрибуции состоит из файла *sdk-version.aar*, который необходимо разместить в директории **../libs** в корне проекта.
Далее нужно перейти в **build.gradle** вашего модуля и добавить зависимости от *.aar-файлов* внутрь блока `dependencies`

> Также здесь необходимо явно добавить транзитивные зависимости библиотек

```
// Ecom Sdk
implementation(files("../libs/ecomsdk-X.Y.Z.aar"))

 // Clickstream
implementation(fileTree(mapOf("dir" to "libs", "include" to listOf("*.jar", "*.aar"))))

implementation("androidx.core:core-ktx:1.12.0")
implementation("androidx.appcompat:appcompat:1.6.1")
implementation("com.google.android.material:material:1.10.0")
implementation("androidx.constraintlayout:constraintlayout:2.1.4")
implementation("androidx.navigation:navigation-ui-ktx:2.7.7")
implementation("androidx.navigation:navigation-fragment-ktx:2.7.7")

// Gson
implementation("com.google.code.gson:gson:2.10.1")

// OkHttp
implementation("com.squareup.okhttp3:okhttp:4.11.0")
implementation("com.squareup.okhttp3:logging-interceptor:4.11.0")

// Retrofit
implementation("com.squareup.retrofit2:retrofit:2.9.0")
implementation("com.squareup.retrofit2:converter-gson:2.9.0")

// Three Ten BP
implementation("com.jakewharton.threetenabp:threetenabp:1.4.7")

// Encrypt
implementation("org.bitbucket.b_c:jose4j:0.9.6")

// Coil
implementation("io.coil-kt:coil-base:2.4.0")
implementation( "io.coil-kt:coil-svg:2.4.0")

// Shimmer
implementation("com.facebook.shimmer:shimmer:0.5.0")

//Dagger 2
implementation("com.google.dagger:dagger:2.48")
ksp("com.google.dagger:dagger-compiler:2.48")
```

В приведенном выше примере указан путь к *aar-файлам*, находящимся в директории *libs* проекта. Если вы разместили их в другом месте, то нужно будет указать ваш путь к файлам. Подробнее смотрите в [документации для Android](https://developer.android.com/studio/projects/android-library#psd-add-aar-jar-dependency)

<br>

## Настройка SDK

Для инициализации SDK необходимо вызвать метод `setup` и передать в него **[EcomSdkSetupConfig](https://sdkpay.github.io/EcomSdkAndroidDoc/data_structures#ecomsdksetupconfig)**

### Kotlin

```
import modern.payments.ecomAndroid.EcomSdk
import modern.payments.ecomAndroid.api.EcomSdkSetupConfig
import modern.payments.ecomAndroid.api.EcomSdkStage
k
val config = EcomSdkSetupConfig(
    context = context,
    stage = EcomSdkStage.PROD,
    disabledFeatures = listOf(),
    enableLoggingByMerchant = true,
    callback = { isSetupSucceed ->
})

EcomSdk.getInstance().setup(config)
```

### Java

```
import modern.payments.ecomAndroid.EcomSdk;
import modern.payments.ecomAndroid.api.EcomSdkSetupConfig;
import modern.payments.ecomAndroid.api.EcomSdkStage; 

EcomSdkSetupConfig ecomSdkSetupConfig =
    new EcomSdkSetupConfig(
        getBaseContext(),
        EcomSdkStage.PROD,
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
