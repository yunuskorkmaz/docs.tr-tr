---
title: Çalışma zamanı config seçenekleri
description: Çalışma zamanı yapılandırma ayarlarını kullanarak .NET Core uygulamalarını nasıl yapılandırıştırmayı öğrenin.
ms.date: 01/21/2020
ms.openlocfilehash: ddf68c30e620a06856f65e71bd050e1b77618f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399163"
---
# <a name="net-core-run-time-configuration-settings"></a>.NET Core çalışma zamanı yapılandırma ayarları

.NET Core, .NET Core uygulamalarının davranışını çalışma zamanında yapılandırmak için yapılandırma dosyalarının ve ortam değişkenlerinin kullanımını destekler. Çalışma zamanı yapılandırması cazip bir seçenektir:

- Bir uygulamanın kaynak koduna sahip değilsiniz veya denetlemiyorsunuz ve bu nedenle bunu programlı olarak yapılandıramadığınız için.

- Uygulamanızın birden çok örneği tek bir sistemde aynı anda çalışır ve her birini optimum performans için yapılandırmak istersiniz.

> [!NOTE]
> Bu belge, devam etmekte olan bir çalışmadır. Burada sunulan bilgilerin eksik veya yanlış olduğunu fark ederseniz, bu konuda bize bildirmek için [bir sorun açın](https://github.com/dotnet/docs/issues) veya sorunu gidermek için bir çekme isteği [gönderin.](https://github.com/dotnet/docs/pulls) dotnet/docs deposu için çekme istekleri gönderme hakkında bilgi için [katılımcının kılavuzuna](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md)bakın.

.NET Core, çalışma zamanı uygulama davranışını yapılandırmak için aşağıdaki mekanizmaları sağlar:

- [Runtimeconfig.json dosyası](#runtimeconfigjson)

- [MSBuild özellikleri](#msbuild-properties)

- [Ortam değişkenleri](#environment-variables)

Bazı yapılandırma değerleri de <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntem çağırarak programlı olarak ayarlanabilir.

Belgelerin bu bölümündeki makaleler kategoriye göre düzenlenir, örneğin, [hata ayıklama](debugging-profiling.md) ve [çöp toplama.](garbage-collector.md) Uygulanabilir olduğu durumlarda, *runtimeconfig.json* dosyaları, MSBuild özellikleri, ortam değişkenleri ve çapraz başvuru için .NET Framework projeleri için *app.config* dosyaları için yapılandırma seçenekleri gösterilir.

## <a name="runtimeconfigjson"></a>runtimeconfig.json

Bir proje [oluşturulduğunda,](../tools/dotnet-build.md)çıktı dizininde bir *[appname].runtimeconfig.json* dosyası oluşturulur. *Runtimeconfig.template.json* dosyası proje dosyasıyla aynı klasörde varsa, içerdiği tüm yapılandırma seçenekleri *[appname].runtimeconfig.json* dosyasında birleştirilir. Uygulamayı kendiniz oluşturuyorsanız, *runtimeconfig.template.json* dosyasına herhangi bir yapılandırma seçeneği koyun. Uygulamayı çalıştırıyorsanız, doğrudan *[appname].runtimeconfig.json* dosyasına ekleyin.

> [!NOTE]
> *[appname].runtimeconfig.json* dosyası sonraki yapılarda üzerine yazılır.

*Runtimeconfig.json* dosyalarının **configProperties** bölümünde çalışma zamanı yapılandırma seçeneklerini belirtin. Bu bölümde şu form vardır:

```json
"configProperties": {
  "config-property-name1": "config-value1",
  "config-property-name2": "config-value2"
}
```

### <a name="example-appnameruntimeconfigjson-file"></a>Örnek [appname].runtimeconfig.json dosyası

Seçenekleri çıktı JSON dosyasına yerlebir ediyorsanız, `runtimeOptions` bunları özelliğin altına yerleştirin.

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

### <a name="example-runtimeconfigtemplatejson-file"></a>Örnek runtimeconfig.template.json dosyası

Seçenekleri şablon JSON dosyasına yerlesanız, özelliği atleyin. `runtimeOptions`

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

Bazı çalışma zamanı yapılandırma seçenekleri, SDK stili .NET Core projelerinin *.csproj* veya *.vbproj* dosyasındaki MSBuild özellikleri kullanılarak ayarlanabilir. MSBuild özellikleri *runtimeconfig.template.json* dosyasında ayarlanan seçeneklerden önceliklidir. *Ayrıca,[appname].runtimeconfig.json* dosyasında ayarladığınız seçeneklerin üzerine de yazılırlar.

Çalışma zamanı davranışını yapılandırmak için MSBuild özelliklerine sahip örnek bir SDK tarzı proje dosyası aşağıda verilmiştir:

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

Çalışma zamanı davranışını yapılandırmak için MSBuild özellikleri, çöp [toplama](garbage-collector.md)gibi her alan için ayrı ayrı makalelerde belirtilmiştir.

## <a name="environment-variables"></a>Ortam değişkenleri

Ortam değişkenleri bazı çalışma zamanı yapılandırma bilgileri sağlamak için kullanılabilir. Çevre değişkenleri olarak belirtilen yapılandırma düğümleri genellikle **COMPlus_** önekine sahiptir.

Ortam değişkenlerini Windows Denetim Masası'ndan, komut satırından veya programlı <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> olarak hem Windows hem de Unix tabanlı sistemlerde arayarak tanımlayabilirsiniz.

Aşağıdaki örnekler, komut satırında bir ortam değişkeninin nasıl ayarlangerektiğini gösterir:

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
