---
title: Varsayılan yoklama-.NET Core
description: Bağımlılıkları bulmak için .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> 'un yoklama mantığına genel bakış.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 020b1d0342ae822021905d2e749037f45031eb22
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70017346"
---
# <a name="default-probing"></a>Varsayılan yoklama

<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Örnek, bir derlemenin bağımlılıklarını bulmaktan sorumludur. Bu makalede <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> örneğin araştırma mantığı açıklanmaktadır.

## <a name="host-configured-probing-properties"></a>Konak yapılandırılmış yoklama özellikleri

Çalışma zamanı başlatıldığında, çalışma zamanı ana bilgisayarı araştırma yollarını yapılandıran <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> adlandırılmış bir yoklama özellikleri kümesi sağlar.

Her yoklama özelliği isteğe bağlıdır.  Varsa, her özellik mutlak yolların ayrılmış bir listesini içeren bir dize değeridir. Sınırlayıcı, Windows üzerinde '; ' ve diğer tüm platformlarda ': '.

|Özellik Adı                 |Açıklama  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Platform ve uygulama derleme dosyası yollarının listesi. |
|`PLATFORM_RESOURCE_ROOTS`       | Uydu kaynak derlemelerinin aranacağı Dizin yollarının listesi. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Yönetilmeyen (yerel) kitaplıkları aramak için Dizin yollarının listesi.        |
|`APP_PATHS`                     | Yönetilen derlemeleri aramak için Dizin yollarının listesi |
|`APP_NI_PATHS`                  | Yönetilen derlemelerin yerel görüntülerini aramak için Dizin yollarının listesi. |

### <a name="how-are-the-properties-populated"></a>Özellikler nasıl doldurulur?

`<myapp>.deps.json` Dosyanın var olup olmadığına bağlı olarak özelliklerin doldurulmasına yönelik iki ana senaryo vardır.

- `*.deps.json` Dosya mevcut olduğunda, araştırma özelliklerini doldurmak için ayrıştırılır.
- `*.deps.json` Dosya mevcut olmadığında, uygulamanın dizininin tüm bağımlılıkları içermesi varsayılır. Dizin içeriği, araştırma özelliklerini doldurmak için kullanılır.

Ayrıca, `*.deps.json` başvurulan tüm çerçeveler için dosyalar benzer şekilde ayrıştırılmaz.

Son olarak, ortam `ADDITIONAL_DEPS` değişkeni ek bağımlılıklar eklemek için kullanılabilir.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Nasıl yaparım? yönetilen koddan yoklama özelliklerini görmek mi istiyorsunuz?

Her özelliğe, yukarıdaki tablodaki Özellik adı <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> ile işlev çağırarak ulaşılabilir.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Nasıl yaparım? araştırma özelliklerinin oluşturulması hata ayıklaması yapılsın mı?

.NET Core çalışma zamanı ana bilgisayarı, belirli ortam değişkenleri etkinleştirildiğinde yararlı izleme iletilerini çıktı olarak izler:

|Ortam değişkeni        |Açıklama  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |İzlemeyi etkinleştirilir.|
|`COREHOST_TRACEFILE=<path>` |Varsayılan `stderr`yerine bir dosya yolu izler.|
|`COREHOST_TRACE_VERBOSITY`  |Ayrıntı düzeyini 1 ' den (en düşük) 4 ' e (en yüksek) ayarlar.|

## <a name="managed-assembly-default-probing"></a>Yönetilen derleme varsayılan yoklama

Yönetilen bir derlemeyi <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> bulma konusunda yoklama yaparken şu sırada görünür:
- İle eşleşen <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` dosyalar (dosya uzantıları kaldırıldıktan sonra).
- Ortak dosya uzantıları ile içindeki `APP_NI_PATHS` yerel görüntü derleme dosyaları.
- Ortak dosya uzantılarıyla `APP_PATHS` içindeki derleme dosyaları.

## <a name="satellite-resource-assembly-probing"></a>Uydu (kaynak) derlemeyi yoklama

Belirli bir kültürün uydu derlemesini bulmak için bir dosya yolları kümesi oluşturun.

İçindeki `PLATFORM_RESOURCE_ROOTS` <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> her yol için, dizeyi, Dizin ayırıcısını, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> dizeyi ve '. dll ' uzantısını ekleyin. `APP_PATHS`

Eşleşen herhangi bir dosya varsa, yüklemeyi ve döndürmeyi deneyin.

## <a name="unmanaged-native-library-probing"></a>Yönetilmeyen (yerel) kitaplık yoklama

Yönetilmeyen bir kitaplığı `NATIVE_DLL_SEARCH_DIRECTORIES` bulma konusunda yoklama yaparken, eşleşen bir kitaplığı arıyor,
