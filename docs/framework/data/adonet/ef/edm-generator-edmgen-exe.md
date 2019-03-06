---
title: EDM Oluşturucu (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 7f06b393cd7e7ccf3d3637d6fb46eb6d983d943a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378060"
---
# <a name="edm-generator-edmgenexe"></a>EDM Oluşturucu (EdmGen.exe)

EdmGen.exe ile çalışmak için kullanılan bir komut satırı aracı olan [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] model ve eşleme dosyaları. Aşağıdakileri yapmak için Edmgen.exe'yi Aracı'nı kullanabilirsiniz:

- Bir veri kaynağına özgü .NET Framework Veri Sağlayıcısı'nı kullanarak bir veri kaynağına bağlanmak ve kavramsal model (.csdl), depolama modelinin (.ssdl) ve tarafından kullanılan eşleme (.msl) dosyaları oluşturma [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için [nasıl yapılır: Model ve eşleme dosyalarını üretmek için Edmgen.exe'yi kullanın](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

- Mevcut bir model doğrulayın. Daha fazla bilgi için [nasıl yapılır: Model ve eşleme dosyalarını doğrulama için Edmgen.exe'yi kullanın](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).

- Bir C# veya Visual Basic kod kavramsal model (.csdl) dosyasından oluşturulan nesne sınıfları içeren bir dosya oluşturun. Daha fazla bilgi için [nasıl yapılır: Nesne Katmanı kodu üretmek için Edmgen.exe'yi kullanın](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md).

- Mevcut bir model için önceden üretilmiş görünümleri içeren bir C# veya Visual Basic kod dosyası oluşturur. Daha fazla bilgi için [nasıl yapılır: Sorgu performansını artırmak için önceden görünümlerin](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).

EdmGen.exe aracına [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] dizin. Çoğu durumda bu C:\windows\Microsoft.NET\Framework\v4.0 içinde bulunur. 64-bit sistemler için bu C:\windows\Microsoft.NET\Framework64\v4.0 içinde bulunur. EdmGen.exe aracı Visual Studio Komut İstemi'nden de erişebilirsiniz (tıklayın **Başlat**, işaret **tüm programlar**, işaret **Microsoft Visual Studio 2010**, işaret **Visual Studio Araçları**ve ardından **Visual Studio 2010 Komut İstemi**).

## <a name="syntax"></a>Sözdizimi

```
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Mod

EdmGen.exe aracını kullanırken, şu modlardan birini belirtmeniz gerekir.

|Mod|Açıklama|
|----------|-----------------|
|`/mode:ValidateArtifacts`|.Csdl .ssdl ve .msl dosyaları doğrular ve herhangi bir hata veya uyarıları görüntüler.<br /><br /> Bu seçenek en az birini gerektirir `/inssdl` veya `/incsdl` bağımsız değişkenler. Varsa `/inmsl` belirtilen `/inssdl` ve `/incsdl` bağımsız değişkenleri gereklidir de.|
|`/mode:FullGeneration`|Belirtilen veritabanı bağlantı bilgilerini kullanır `/connectionstring` nesne katmanı seçeneği ve .csdl, .ssdl .msl, oluşturur ve dosyaları görüntüleyin.<br /><br /> Bu seçenek gerektirir bir `/connectionstring` bağımsız değişkeni ve ya da bir `/project` bağımsız değişkeni veya `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace`, ve `/entitycontainer` bağımsız değişkenler.|
|`/mode:FromSSDLGeneration`|Belirtilen .ssdl dosyasından .csdl ve .msl dosyaları, kaynak kodu ve görünümler oluşturur.<br /><br /> Bu seçenek gerektirir `/inssdl` bağımsız değişkeni ve ya da bir `/project` bağımsız değişkeni veya `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` ve `/entitycontainer` bağımsız değişkenler.|
|`/mode:EntityClassGeneration`|.Csdl dosyasından oluşturulan sınıflar içeren kaynak kodu dosyası oluşturur.<br /><br /> Bu seçenek gerektirir `/incsdl` bağımsız değişkeni ve ya da `/project` bağımsız değişkeni veya `/outobjectlayer` bağımsız değişken. `/language` Bağımsız değişken isteğe bağlıdır.|
|`/mode:ViewGeneration`|.csdl, .ssdl .msl dosyaları oluşturulan görünümleri içeren bir kaynak kodu dosyası oluşturur.<br /><br /> Bu seçenek gerektirir `/inssdl`, `/incsdl`, `/inmsl,` ve her iki `/project` veya `/outviews` bağımsız değişkenler. `/language` Bağımsız değişken isteğe bağlıdır.|

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|`/p[roject]:`\<dize >|Proje adını belirtir. Proje adı varsayılan olarak ayarlamak, model ve eşleme dosyaları, nesne kaynak dosyasının adını ve görünümü nesil kaynak dosyasının adını adını ad alanı için kullanılır. Varlık kapsayıcı adı kümesine \<Proje > bağlamı.|
|`/prov[ider]:`\<dize >|Adını [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] depolama modeli (.ssdl) dosyası oluşturmak için kullanılacak veri sağlayıcısı. Varsayılan sağlayıcıdır [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] SQL Server için veri sağlayıcısı (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|
|`/c[onnectionstring]:`\<bağlantı dizesi >|Veri kaynağına bağlanmak için kullanılan dizeyi belirtir.|
|`/incsdl:`\<Dosya >|.csdl dosya veya dizin .csdl dosyaların nerede olduğunu belirtir. Birden çok dizini veya .csdl dosyaları belirtmek için bu bağımsız değişken birden çok kez belirtilebilir. Birden çok dizini belirten sınıflar oluşturmak için kullanışlı olabilir (`/mode:EntityClassGeneration`) veya görünümleri (`/mode:ViewGeneration`) kavramsal model çeşitli dosyalar arasında bölüneceğini zaman. Birden çok modeli doğrulamak istediğiniz zaman da yararlı olabilir (`/mode:ValidateArtifacts`).|
|`/refcsdl:`\<Dosya >|Ek .csdl dosya veya dosyalar kaynak .csdl dosyadaki tüm başvuruları çözümlemek için kullanılan belirtir. (Kaynak .csdl dosyası değil, tarafından belirtilen dosya `/incsdl` seçeneği). `/refcsdl` Dosyası kaynak .csdl dosyası bağımlı olduğu türleri içerir. Bu bağımsız değişken birden çok kez belirtilebilir.|
|`/inmsl:`\<Dosya >|.msl dosya veya dizin .msl dosyaların nerede olduğunu belirtir. Birden çok dizini veya .msl dosyaları belirtmek için bu bağımsız değişken birden çok kez belirtilebilir. Birden çok dizini belirtme görünümleri oluşturmak için kullanışlı olabilir (`/mode:ViewGeneration`) kavramsal model çeşitli dosyalar arasında bölüneceğini zaman. Birden çok modeli doğrulamak istediğiniz zaman da yararlı olabilir (`/mode:ValidateArtifacts`).|
|`/inssdl:`\<Dosya >|.Ssdl dosya veya .ssdl dosyasının bulunduğu dizini belirtir. Birden çok dizini veya .ssdl dosyaları belirtmek için bu bağımsız değişken birden çok kez belirtilebilir. Birden çok modeli doğrulamak istediğiniz durumlarda bu kullanışlı olabilir `(/mode:ValidateArtifacts)`.|
|`/outcsdl:`\<Dosya >|Oluşturulacak .csdl dosyasının adını belirtir.|
|`/outmsl:`\<Dosya >|Oluşturulacak .msl dosyasının adını belirtir.|
|`/outssdl:`\<Dosya >|Oluşturulacak .ssdl dosyasının adını belirtir.|
|`/outobjectlayer:`\<Dosya >|.Csdl dosyasından oluşturulan nesneleri içeren kaynak kodu dosyasının adını belirtir.|
|`/outviews:`\<Dosya >|Oluşturulan görünümleri içeren kaynak kodu dosyasının adını belirtir.|
|`/language:`[VB&#124;CSharp]|Oluşturulan kaynak kodu dosyaları dilini belirtir. C# dil Varsayılanları.|
|`/namespace:`\<dize >|Kullanılacak modeli ad alanını belirtir. Ad alanı çalıştırırken .csdl dosyasında ayarlanır `/mode:FullGeneration` veya `/mode:FromSSDLGeneration`. Ad alanı çalıştırırken kullanılmayan `/mode:EntityClassGeneration`.|
|`/entitycontainer:`\<dize >|Uygulamak için bir ad belirtir `<EntityContainer>` oluşturulan model ve eşleme dosyalarını öğesi.|
|`/pl[uralize]`|Singulars ve gerçekleştirebilse için İngilizce dil kuralları uygular `Entity`, `EntitySet`, ve `NavigationProperty` adlarında kavramsal model. Bu seçenek, aşağıdaki eylemleri gerçekleştirir:<br /><br /> -Tüm olun `EntityType` tekil adları.<br />-Tüm olun `EntitySet` çoğul adları.<br />-İçin her `NavigationProperty` en fazla bir varlık döndüren, adı tekil yapın.<br />-İçin her `NavigationProperty` birden fazla varlık getiren, adın çoğul olun.|
|`/SuppressForeignKeyProperties or /nofk`|Yabancı anahtar sütunları kavramsal modelin varlık türlerini skaler özellikleri olarak gösterilen engeller.|
|`/help` veya `?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/nologo`|Telif hakkı iletisini görüntülenmesini bastırır.|
|`/targetversion:` \<dize >|Oluşturulan kodu derlemek için kullanılacak .NET Framework sürümü. Desteklenen 4 ve 4.5 sürümleridir. Varsayılan olarak 4.|

## <a name="in-this-section"></a>Bu Bölümde

[Nasıl yapılır: Model ve eşleme dosyalarını üretmek için Edmgen.exe'yi kullanın](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Nasıl yapılır: Nesne Katmanı kodu üretmek için Edmgen.exe'yi kullanın](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Nasıl yapılır: Model ve eşleme dosyalarını doğrulama için Edmgen.exe'yi kullanın](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Varlık Veri Modeli](../../../../../docs/framework/data/adonet/entity-data-model.md)
- [CSDL, SSDL ve MSL Belirtimleri](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
