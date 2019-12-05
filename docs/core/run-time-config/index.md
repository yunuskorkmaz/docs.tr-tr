---
title: Çalışma zamanı yapılandırması
description: Çalışma zamanı yapılandırma ayarlarını kullanarak .NET Core uygulamalarını nasıl yapılandıracağınızı öğrenin.
ms.date: 11/13/2019
ms.openlocfilehash: 2665026347e94d26026821beb2bfcf8441f755f6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801922"
---
# <a name="net-core-run-time-configuration-settings"></a>.NET Core çalışma zamanı yapılandırma ayarları

.NET Core, çalışma zamanında .NET Core uygulamalarının davranışını yapılandırmak için yapılandırma dosyalarının ve ortam değişkenlerinin kullanımını destekler. Çalışma zamanı yapılandırması, şu durumlarda çekici bir seçenektir:

- Bir uygulama için kaynak kodu sahibi değilsiniz veya denetiminiz yoktur, bu nedenle program aracılığıyla yapılandıramamaktır.

- Uygulamanızın birden çok örneği tek bir sistemde aynı anda çalışır ve her birini en iyi performans için yapılandırmak istiyorsunuz.

> [!NOTE]
> Bu belge devam eden bir çalışmadır. Burada sunulan bilgilerin eksik veya yanlış olduğunu fark ederseniz, bunun hakkında bilgi sahibi olmak için [bir sorun açın](https://github.com/dotnet/docs/issues) veya sorunu çözmek için [bir çekme isteği gönderin](https://github.com/dotnet/docs/pulls) . DotNet/docs deposu için çekme istekleri gönderme hakkında daha fazla bilgi için bkz. [katkıda bulunan Kılavuzu](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).

.NET Core, çalışma zamanında uygulamaları yapılandırmak için aşağıdaki mekanizmaları sağlar:

- [Runtimeconfig. JSON dosyası](#runtimeconfigjson)

- [Ortam değişkenleri](#environment-variables)

Belgelerin bu bölümündeki makaleler, örneğin, hata ayıklama ve çöp toplama gibi kategoriye göre düzenlenmiştir. Uygun olduğunda, *runtimeconfig. JSON* (yalnızca .NET Core), *app. config* (yalnızca .NET Framework) ve ortam değişkenleri için yapılandırma seçenekleri gösterilir.

## <a name="runtimeconfigjson"></a>runtimeconfig. JSON

Uygulamanın *runtimeconfig. JSON* dosyasının **ConfigProperties** bölümünde çalışma zamanı yapılandırma seçeneklerini belirtin. Bu bölüm şu biçimdedir:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

Örnek bir dosya aşağıda verilmiştir:

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

*Runtimeconfig. JSON* dosyası, [DotNet Build](../tools/dotnet-build.md) komutuyla derleme dizininde otomatik olarak oluşturulur. Visual Studio 'da **Build** Menu seçeneğini belirlediğinizde de oluşturulur. Sonra dosyayı, oluşturulduktan sonra düzenleyebilirsiniz.

Bazı yapılandırma değerleri de <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemi çağırarak programlı olarak ayarlanabilir.

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
