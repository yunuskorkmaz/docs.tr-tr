---
title: Varsayılan yoklama-.NET Core
description: Bağımlılıkları bulmak için .NET Core 'un System. Runtime. Loader. AssemblyLoadContext. Default araştırma mantığına genel bakış.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031831"
---
# <a name="default-probing"></a>Varsayılan yoklama

<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> örneği, bir derlemenin bağımlılıklarını bulmaktan sorumludur. Bu makalede <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> örneğinin yoklama mantığı açıklanmaktadır.

## <a name="host-configured-probing-properties"></a>Konak yapılandırılmış yoklama özellikleri

Çalışma zamanı başlatıldığında, çalışma zamanı ana bilgisayarı <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> araştırma yollarını yapılandıran adlandırılmış bir yoklama özellikleri kümesi sağlar.

Her yoklama özelliği isteğe bağlıdır. Varsa, her özellik mutlak yolların ayrılmış bir listesini içeren bir dize değeridir. Sınırlayıcı, Windows üzerinde '; ' ve diğer tüm platformlarda ': '.

|Özellik Adı                 |Açıklama  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Platform ve uygulama derleme dosyası yollarının listesi. |
|`PLATFORM_RESOURCE_ROOTS`       | Uydu kaynak derlemelerinin aranacağı Dizin yollarının listesi. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Yönetilmeyen (yerel) kitaplıkları aramak için Dizin yollarının listesi.        |
|`APP_PATHS`                     | Yönetilen derlemeleri aramak için Dizin yollarının listesi. |
|`APP_NI_PATHS`                  | Yönetilen derlemelerin yerel görüntülerini aramak için Dizin yollarının listesi. |

### <a name="how-are-the-properties-populated"></a>Özellikler nasıl doldurulur?

*\<myapp >. Deps. JSON* dosyasının var olup olmadığına bağlı olarak özelliklerin doldurulmasına yönelik iki ana senaryo vardır.

- *\*. Deps. JSON* dosyası mevcut olduğunda, araştırma özelliklerini doldurmak için ayrıştırılır.
- *\*. Deps. JSON* dosyası mevcut olmadığında, uygulamanın dizininin tüm bağımlılıkları içermesi varsayılır. Dizin içeriği, araştırma özelliklerini doldurmak için kullanılır.

Ayrıca, başvurulan tüm çerçeveler için *\*. Deps. JSON* dosyaları benzer şekilde ayrıştırılmaz.

Son olarak, `ADDITIONAL_DEPS` ortam değişkeni ek bağımlılıklar eklemek için kullanılabilir.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Nasıl yaparım? yönetilen koddan yoklama özelliklerini görmek mi istiyorsunuz?

Her özelliğe, yukarıdaki tablodaki Özellik adı ile <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> işlevi çağırarak ulaşılabilir.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Nasıl yaparım? araştırma özelliklerinin oluşturulması hata ayıklaması yapılsın mı?

.NET Core çalışma zamanı ana bilgisayarı, belirli ortam değişkenleri etkinleştirildiğinde yararlı izleme iletilerini çıktı olarak izler:

|Ortam değişkeni        |Açıklama  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |İzlemeyi etkinleştirilir.|
|`COREHOST_TRACEFILE=<path>` |Varsayılan `stderr`yerine bir dosya yolu izler.|
|`COREHOST_TRACE_VERBOSITY`  |Ayrıntı düzeyini 1 ' den (en düşük) 4 ' e (en yüksek) ayarlar.|

## <a name="managed-assembly-default-probing"></a>Yönetilen derleme varsayılan yoklama

Yönetilen bir derlemeyi bulma konusunda yoklama yaparken <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> şu zamanda sırayla görünür:

- `TRUSTED_PLATFORM_ASSEMBLIES` <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> eşleşen dosyalar (dosya uzantıları kaldırıldıktan sonra).
- Ortak dosya uzantılarıyla `APP_NI_PATHS` içindeki yerel görüntü derleme dosyaları.
- Ortak dosya uzantılarına sahip `APP_PATHS` içindeki derleme dosyaları.

## <a name="satellite-resource-assembly-probing"></a>Uydu (kaynak) derlemeyi yoklama

Belirli bir kültürün uydu derlemesini bulmak için bir dosya yolları kümesi oluşturun.

`PLATFORM_RESOURCE_ROOTS` içindeki her yol için, `APP_PATHS`<xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> dizesini, Dizin ayırıcısını, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> dizeyi ve '. dll ' uzantısını ekleyin.

Eşleşen herhangi bir dosya varsa, yüklemeyi ve döndürmeyi deneyin.

## <a name="unmanaged-native-library-probing"></a>Yönetilmeyen (yerel) kitaplık yoklama

Yönetilmeyen bir kitaplığı bulmaya yönelik yoklama yaparken, `NATIVE_DLL_SEARCH_DIRECTORIES` eşleşen bir kitaplığı arayarak aranır.
