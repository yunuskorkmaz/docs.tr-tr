---
title: Varsayılan yoklama-.NET Core
description: Bağımlılıkları bulmak için .NET Core 'un System. Runtime. Loader. AssemblyLoadContext. Default araştırma mantığına genel bakış.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 13ce4c7de5f6ce1b76b2e61db810c0f19717540f
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608421"
---
# <a name="default-probing"></a>Varsayılan yoklama

<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>Örnek, bir derlemenin bağımlılıklarını bulmaktan sorumludur. Bu makalede <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Örneğin araştırma mantığı açıklanmaktadır.

## <a name="host-configured-probing-properties"></a>Konak yapılandırılmış yoklama özellikleri

Çalışma zamanı başlatıldığında, çalışma zamanı ana bilgisayarı araştırma yollarını yapılandıran adlandırılmış bir yoklama özellikleri kümesi sağlar <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> .

Her yoklama özelliği isteğe bağlıdır. Varsa, her özellik mutlak yolların ayrılmış bir listesini içeren bir dize değeridir. Sınırlayıcı, Windows üzerinde '; ' ve diğer tüm platformlarda ': '.

|Özellik Adı                 |Açıklama  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Platform ve uygulama derleme dosyası yollarının listesi. |
|`PLATFORM_RESOURCE_ROOTS`       | Uydu kaynak derlemelerinin aranacağı Dizin yollarının listesi. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Yönetilmeyen (yerel) kitaplıkları aramak için Dizin yollarının listesi.        |
|`APP_PATHS`                     | Yönetilen derlemeleri aramak için Dizin yollarının listesi. |
|`APP_NI_PATHS`                  | Yönetilen derlemelerin yerel görüntülerini aramak için Dizin yollarının listesi. |

### <a name="how-are-the-properties-populated"></a>Özellikler nasıl doldurulur?

* \<myapp>.deps.js* dosyanın var olup olmadığına bağlı olarak özelliklerin doldurulmasına yönelik iki ana senaryo vardır.

- Dosyadaki * \*.deps.js* olduğunda, araştırma özelliklerini doldurmak için ayrıştırılır.
- Dosyadaki * \*.deps.js* mevcut olmadığında, uygulamanın dizininin tüm bağımlılıkları içermesi varsayılır. Dizin içeriği, araştırma özelliklerini doldurmak için kullanılır.

Ayrıca, başvurulan tüm çerçeveler için dosyalardaki * \*.deps.js* benzer şekilde ayrıştırılmaz.

Son olarak, ortam değişkeni `ADDITIONAL_DEPS` ek bağımlılıklar eklemek için kullanılabilir.  `dotnet.exe` Ayrıca, `--additional-deps` uygulamanın başlangıcında bu değeri ayarlamak için isteğe bağlı bir parametre içerir.

`APP_PATHS`Ve `APP_NI_PATHS` özellikleri varsayılan olarak doldurulmaz ve çoğu uygulama için atlanır.

Uygulama tarafından kullanılan dosyalardaki tüm * \*.deps.js* listesine aracılığıyla erişilebilir `System.AppContext.GetData("APP_CONTEXT_DEPS_FILES")` .

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Nasıl yaparım? yönetilen koddan yoklama özelliklerini görmek mi istiyorsunuz?

Her özelliğe, <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> Yukarıdaki tablodaki Özellik adı ile işlev çağırarak ulaşılabilir.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Nasıl yaparım? araştırma özelliklerinin oluşturulması hata ayıklaması yapılsın mı?

.NET Core çalışma zamanı ana bilgisayarı, belirli ortam değişkenleri etkinleştirildiğinde yararlı izleme iletilerini çıktı olarak izler:

|Ortam değişkeni        |Açıklama  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |İzlemeyi etkinleştirilir.|
|`COREHOST_TRACEFILE=<path>` |Varsayılan yerine bir dosya yolu izler `stderr` .|
|`COREHOST_TRACE_VERBOSITY`  |Ayrıntı düzeyini 1 ' den (en düşük) 4 ' e (en yüksek) ayarlar.|

## <a name="managed-assembly-default-probing"></a>Yönetilen derleme varsayılan yoklama

Yönetilen bir derlemeyi bulma konusunda yoklama yaparken <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Şu sırada görünür:

- İle eşleşen dosyalar <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` (dosya uzantıları kaldırıldıktan sonra).
- Ortak dosya uzantıları ile içindeki yerel görüntü derleme dosyaları `APP_NI_PATHS` .
- `APP_PATHS`Ortak dosya uzantılarıyla içindeki derleme dosyaları.

## <a name="satellite-resource-assembly-probing"></a>Uydu (kaynak) derlemeyi yoklama

Belirli bir kültürün uydu derlemesini bulmak için bir dosya yolları kümesi oluşturun.

İçindeki her yol için, `PLATFORM_RESOURCE_ROOTS` `APP_PATHS` <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> dizeyi, Dizin ayırıcısını, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> dizeyi ve '. dll ' uzantısını ekleyin.

Eşleşen herhangi bir dosya varsa, yüklemeyi ve döndürmeyi deneyin.

## <a name="unmanaged-native-library-probing"></a>Yönetilmeyen (yerel) kitaplık yoklama

Yönetilmeyen bir kitaplığı bulmaya yönelik yoklama yaparken, bu, `NATIVE_DLL_SEARCH_DIRECTORIES` eşleşen bir kitaplığı arıyor.
