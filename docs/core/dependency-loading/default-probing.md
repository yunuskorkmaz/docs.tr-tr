---
title: Varsayılan sondalama - .NET Core
description: .NET Core's System.Runtime.Loader.AssemblyLoadContext.Default sondalama mantığı bağımlılıkları bulmak için genel bakış.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399093"
---
# <a name="default-probing"></a>Varsayılan sondalama

Örnek, <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> bir derlemenin bağımlılıklarını bulmakla yükümlüdür. Bu <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> makalede, örneğin sondalama mantığı açıklanmaktadır.

## <a name="host-configured-probing-properties"></a>Barındırış yapılandırılmış sondalama özellikleri

Çalışma zamanı başlatıldığında, çalışma zamanı ana bilgisayarı <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> sonda yollarını yapılandıran adlandırılmış sonda özellikleri kümesi sağlar.

Her sondalama özelliği isteğe bağlıdır. Varsa, her özellik, salt yolların sınırlı bir listesini içeren bir dize değeridir. Delimiter, Windows'da ';' ve diğer tüm platformlarda ':' olarak bilinir.

|Özellik Adı                 |Açıklama  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Platform ve uygulama derleme dosya yollarının listesi. |
|`PLATFORM_RESOURCE_ROOTS`       | Uydu kaynak derlemelerini aramak için dizin yolları listesi. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Yönetilmeyen (yerel) kitaplıkları aramak için dizin yolları listesi.        |
|`APP_PATHS`                     | Yönetilen derlemeleri aramak için dizin yolları listesi. |
|`APP_NI_PATHS`                  | Yönetilen derlemelerin yerel görüntülerini aramak için dizin yolları listesi. |

### <a name="how-are-the-properties-populated"></a>Mülkler nasıl doldurulur?

* \<Myapp>.deps.json* dosyasının var olup olmadığına bağlı olarak özellikleri doldurmak için iki ana senaryo vardır.

- .deps.json dosyası bulunduğunda, sonlama özelliklerini doldurmak için ayrıştırılır. * \**
- .deps.json dosyası yoksa, uygulamanın dizininin tüm bağımlılıkları içerdiği varsayılır. * \** Dizin içeriği sondalama özelliklerini doldurmak için kullanılır.

Ayrıca, başvurulan çerçeveler için * \*.deps.json* dosyaları benzer şekilde ayrıştı.

Son olarak `ADDITIONAL_DEPS` ortam değişkeni ek bağımlılıklar eklemek için kullanılabilir.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Yönetilen koddaki sondalama özelliklerini nasıl görebiliyorum?

Her özellik yukarıdaki tablodan özellik adı ile <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> işlevi çağırarak kullanılabilir.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Sonlama özelliklerinin inşaatını nasıl ayıka ait olurum?

.NET Core çalışma zamanı ana bilgisayarı, belirli ortam değişkenleri etkinleştirildiğinde yararlı izleme iletileri çıkaracaktır:

|Çevre Değişkeni        |Açıklama  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |İzlemeyi sağlar.|
|`COREHOST_TRACEFILE=<path>` |Varsayılan `stderr`yerine bir dosya yoluna izler.|
|`COREHOST_TRACE_VERBOSITY`  |Ayrıntılılığı 1 (en düşük) ile 4 (en yüksek) arasında ayarlar.|

## <a name="managed-assembly-default-probing"></a>Yönetilen derleme varsayılan sondalama

Yönetilen bir derlemeyi bulmak için <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> sondalama yaparken, aşağıdakileri sırayla bakar:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> In `TRUSTED_PLATFORM_ASSEMBLIES` ile eşleşen dosyalar (dosya uzantılarını kaldırdıktan sonra).
- Ortak dosya uzantıları `APP_NI_PATHS` ile yerel görüntü derleme dosyaları.
- Ortak dosya `APP_PATHS` uzantıları ile derleme dosyaları.

## <a name="satellite-resource-assembly-probing"></a>Uydu (kaynak) montaj sondalama

Belirli bir kültür için uydu derlemesi bulmak için bir dosya yolu kümesi oluşturun.

Her yol `PLATFORM_RESOURCE_ROOTS` için `APP_PATHS`ve sonra <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> , dize, bir dizin ayırıcı, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> dize ve uzantısı '.dll' ekler.

Eşleşen bir dosya varsa, yüklemeyi ve döndürmeyi dene.

## <a name="unmanaged-native-library-probing"></a>Yönetilmeyen (yerel) kitaplık sondalama

Yönetilmeyen bir kitaplığı bulmak için `NATIVE_DLL_SEARCH_DIRECTORIES` araştırma yaparken, eşleşen bir kitaplık aranır.
