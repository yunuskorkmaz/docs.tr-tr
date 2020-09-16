---
title: Çalışma zamanı yapılandırma seçenekleri
description: Çalışma zamanı yapılandırma ayarlarını kullanarak .NET Core uygulamalarını nasıl yapılandıracağınızı öğrenin.
ms.date: 01/21/2020
ms.openlocfilehash: 21673a221d0f21202febf4730b955da66132d5f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538204"
---
# <a name="net-core-run-time-configuration-settings"></a>.NET Core çalışma zamanı yapılandırma ayarları

.NET Core, çalışma zamanında .NET Core uygulamalarının davranışını yapılandırmak için yapılandırma dosyalarının ve ortam değişkenlerinin kullanımını destekler. Çalışma zamanı yapılandırması, şu durumlarda çekici bir seçenektir:

- Bir uygulama için kaynak kodu sahibi değilsiniz veya denetiminiz yoktur, bu nedenle program aracılığıyla yapılandıramamaktır.

- Uygulamanızın birden çok örneği tek bir sistemde aynı anda çalışır ve her birini en iyi performans için yapılandırmak istiyorsunuz.

> [!NOTE]
> Bu belge devam eden bir çalışmadır. Burada sunulan bilgilerin eksik veya yanlış olduğunu fark ederseniz, bunun hakkında bilgi sahibi olmak için [bir sorun açın](https://github.com/dotnet/docs/issues) veya sorunu çözmek için [bir çekme isteği gönderin](https://github.com/dotnet/docs/pulls) . DotNet/docs deposu için çekme istekleri gönderme hakkında daha fazla bilgi için bkz. [katkıda bulunan Kılavuzu](/contribute/dotnet/dotnet-contribute).

.NET Core, çalışma zamanında uygulama davranışını yapılandırmak için aşağıdaki mekanizmaları sağlar:

- [Dosyadakiruntimeconfig.js](#runtimeconfigjson)

- [MSBuild özellikleri](#msbuild-properties)

- [Ortam değişkenleri](#environment-variables)

> [!TIP]
> Bir ortam değişkeni kullanarak bir çalışma zamanı seçeneğinin yapılandırılması, ayarı tüm .NET Core uygulamalarına uygular. *runtimeconfig.js* veya proje dosyasındaki bir çalışma zamanı seçeneğinin yapılandırılması, ayarı yalnızca bu uygulamaya uygular.

Bazı yapılandırma değerleri, yöntemi çağırarak programlı bir şekilde ayarlanabilir <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> .

Belgelerin bu bölümündeki makaleler, bir kategoriye göre düzenlenir, örneğin [hata ayıklama](debugging-profiling.md) ve [çöp toplama](garbage-collector.md). Uygun olduğunda, yapılandırma seçenekleri *runtimeconfig.js* dosya, MSBuild özellikleri, ortam değişkenleri ve .NET Framework projelerine yönelik çapraz başvuru *app.config* dosyaları için gösterilir.

## <a name="runtimeconfigjson"></a>Üzerinde runtimeconfig.js

Bir proje [oluşturulduğunda, çıkış](../tools/dotnet-build.md)dizininde bir *[AppName] .runtimeconfig.js* dosyası oluşturulur. Dosyadaki bir *runtimeconfig.template.js* proje dosyası ile aynı klasörde mevcutsa, içerdiği tüm yapılandırma seçenekleri dosyada *[AppName] .runtimeconfig.js* birleştirilir. Uygulamayı kendiniz oluşturuyorsanız, dosyadaki *runtimeconfig.template.js* yapılandırma seçeneklerini yerleştirin. Uygulamayı yalnızca çalıştırıyorsanız, dosyayı doğrudan *[AppName] .runtimeconfig.js* dosyasına ekleyin.

> [!NOTE]
> Dosyadaki *[AppName] .runtimeconfig.js* , sonraki derlemelerde üzerine yazılır.

Dosyalardaki *runtimeconfig.js* **ConfigProperties** bölümünde çalışma zamanı yapılandırma seçeneklerini belirtin. Bu bölüm şu biçimdedir:

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Örnek [AppName] dosya üzerinde .runtimeconfig.js

Seçenekleri çıkış JSON dosyasına yerleştiriyorsanız, özelliğin altına yerleştirin `runtimeOptions` .

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

### <a name="example-runtimeconfigtemplatejson-file"></a>Dosyada örnek runtimeconfig.template.js

Seçenekleri şablon JSON dosyasına yerleştiriyorsanız, `runtimeOptions` özelliği atlayın.

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

Bazı çalışma zamanı yapılandırma seçenekleri, SDK stili .NET Core projelerinin *. csproj* veya *. vbproj* dosyasındaki MSBuild özellikleri kullanılarak ayarlanabilir. MSBuild özellikleri dosyadaki *runtimeconfig.template.js* ayarlanan seçeneklere göre önceliklidir. Ayrıca, derleme zamanında dosyadaki *[AppName] .runtimeconfig.js* ayarladığınız seçeneklerin üzerine yazar.

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

Çalışma zamanı davranışını yapılandırmaya yönelik MSBuild özellikleri, her bir alana yönelik her bir makalede (örneğin, [çöp toplama](garbage-collector.md)) belirtilmiştir. Bunlar ayrıca SDK stili projelerin MSBuild özellikleri başvurusunun [çalışma zamanı yapılandırması](../project-sdk/msbuild-props.md#run-time-configuration-properties) bölümünde listelenir.

## <a name="environment-variables"></a>Ortam değişkenleri

Ortam değişkenleri, bazı çalışma zamanı yapılandırma bilgilerini sağlamak için kullanılabilir. Bir ortam değişkeni kullanarak bir çalışma zamanı seçeneğinin yapılandırılması, ayarı tüm .NET Core uygulamalarına uygular. Ortam değişkenleri olarak belirtilen yapılandırma örneklerinin genellikle **COMPlus_** öneki vardır.

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
