---
title: Çalışma zamanı yapılandırma seçenekleri
description: Çalışma zamanı yapılandırma ayarlarını kullanarak .NET Core uygulamalarını nasıl yapılandıracağınızı öğrenin.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733443"
---
# <a name="net-core-run-time-configuration-settings"></a>.NET Core çalışma zamanı yapılandırma ayarları

.NET Core, çalışma zamanında .NET Core uygulamalarının davranışını yapılandırmak için yapılandırma dosyalarının ve ortam değişkenlerinin kullanımını destekler. Çalışma zamanı yapılandırması, şu durumlarda çekici bir seçenektir:

- Bir uygulama için kaynak kodu sahibi değilsiniz veya denetiminiz yoktur, bu nedenle program aracılığıyla yapılandıramamaktır.

- Uygulamanızın birden çok örneği tek bir sistemde aynı anda çalışır ve her birini en iyi performans için yapılandırmak istiyorsunuz.

> [!NOTE]
> Bu belge devam eden bir çalışmadır. Burada sunulan bilgilerin eksik veya yanlış olduğunu fark ederseniz, bunun hakkında bilgi sahibi olmak için [bir sorun açın](https://github.com/dotnet/docs/issues) veya sorunu çözmek için [bir çekme isteği gönderin](https://github.com/dotnet/docs/pulls) . DotNet/docs deposu için çekme istekleri gönderme hakkında daha fazla bilgi için bkz. [katkıda bulunan Kılavuzu](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).

.NET Core, çalışma zamanı uygulama davranışını yapılandırmak için aşağıdaki mekanizmaları sağlar:

- [Runtimeconfig. JSON dosyası](#runtimeconfigjson)

- [MSBuild özellikleri](#msbuild-properties)

- [Ortam değişkenleri](#environment-variables)

Bazı yapılandırma değerleri de <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemi çağırarak programlı olarak ayarlanabilir.

Belgelerin bu bölümündeki makaleler, bir kategoriye göre düzenlenir, örneğin [hata ayıklama](debugging-profiling.md) ve [çöp toplama](garbage-collector.md). Uygun olduğunda, yapılandırma seçenekleri için *runtimeconfig. JSON* dosyaları, MSBuild özellikleri, ortam değişkenleri ve .NET Framework projeler için çapraz başvuru, *app. config* dosyaları için gösterilir.

## <a name="runtimeconfigjson"></a>runtimeconfig. JSON

Bir proje [oluşturulduğunda, çıkış](../tools/dotnet-build.md)dizininde *[AppName]. runtimeconfig. JSON* dosyası oluşturulur. Proje dosyasıyla aynı klasörde bir *runtimeconfig. Template. JSON* dosyası varsa, içerdiği tüm yapılandırma seçenekleri *[AppName]. runtimeconfig. JSON* dosyasında birleştirilir. Uygulamayı kendiniz oluşturuyorsanız, tüm yapılandırma seçeneklerini *runtimeconfig. Template. JSON* dosyasına koyun. Uygulamayı yalnızca çalıştırıyorsanız doğrudan *[AppName]. runtimeconfig. JSON* dosyasına ekleyin.

> [!NOTE]
> *[AppName]. runtimeconfig. JSON* dosyasının sonraki yapılarda üzerine yazılır.

*Runtimeconfig. JSON* dosyalarının **ConfigProperties** bölümünde çalışma zamanı yapılandırma seçeneklerini belirtin. Bu bölüm şu biçimdedir:

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Örnek [AppName]. runtimeconfig. JSON dosyası

Seçenekleri çıkış JSON dosyasına yerleştiriyorsanız, `runtimeOptions` özelliği altına yerleştirin.

```json
{
  "runtimeOptions": {
    "tfm": "netcoreapp3.1",
    "framework": {
      "name": "Microsoft.NETCore.App",
      "version": "3.1.0"
    },
    "configProperties": {
      "System.GC.Concurrent": false,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

### <a name="example-runtimeconfigtemplatejson-file"></a>Örnek runtimeconfig. Template. JSON dosyası

Şablon JSON dosyasına seçenekleri yerleştiriyorsanız `runtimeOptions` özelliğini atlayın.

```json
{
  "configProperties": {
    "System.GC.Concurrent": false,
    "System.Threading.ThreadPool.MinThreads": "4",
    "System.Threading.ThreadPool.MaxThreads": "25"
  }
}
```

## <a name="msbuild-properties"></a>MSBuild özellikleri

Bazı çalışma zamanı yapılandırma seçenekleri, SDK stili .NET Core projelerinin *. csproj* veya *. vbproj* dosyasındaki MSBuild özellikleri kullanılarak ayarlanabilir. MSBuild özellikleri, *runtimeconfig. Template. JSON* dosyasında ayarlanan seçeneklere göre önceliklidir. Ayrıca derleme zamanında *[AppName]. runtimeconfig. JSON* dosyasında ayarladığınız seçeneklerin üzerine yazar.

Aşağıda, çalışma zamanı davranışını yapılandırmak için MSBuild özelliklerine sahip örnek bir SDK stili proje dosyası verilmiştir:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
    <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
  </PropertyGroup>

</Project>
```

Çalışma zamanı davranışını yapılandırmaya yönelik MSBuild özellikleri, her bir alana yönelik her bir makalede (örneğin, [çöp toplama](garbage-collector.md)) belirtilmiştir.

## <a name="environment-variables"></a>Ortam değişkenleri

Ortam değişkenleri, bazı çalışma zamanı yapılandırma bilgilerini sağlamak için kullanılabilir. Ortam değişkenleri olarak belirtilen yapılandırma örneklerinin genellikle **COMPlus_** öneki vardır.

Ortam değişkenlerini Windows Denetim masasından, komut satırında veya <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> yöntemini hem Windows hem de UNIX tabanlı sistemlerde çağırarak programlı bir şekilde tanımlayabilirsiniz.

Aşağıdaki örneklerde, komut satırında bir ortam değişkeninin nasıl ayarlanacağı gösterilmektedir:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
