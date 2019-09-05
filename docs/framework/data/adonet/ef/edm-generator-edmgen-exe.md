---
title: EDM Oluşturucu (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 688989fea6037cc989267e14b103210c2a995afa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251624"
---
# <a name="edm-generator-edmgenexe"></a>EDM Oluşturucu (EdmGen.exe)

EdmGen. exe, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] model ve eşleme dosyalarıyla çalışmak için kullanılan bir komut satırı aracıdır. EdmGen. exe aracını kullanarak şunları gerçekleştirebilirsiniz:

- Veri kaynağına özgü .NET Framework veri sağlayıcısı kullanarak bir veri kaynağına bağlanın ve tarafından [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]kullanılan kavramsal model (. csdl), depolama modeli (. ssdl) ve eşleme (. MSL) dosyalarını oluşturun. Daha fazla bilgi için [nasıl yapılır: Modeli ve eşleme dosyalarını](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)oluşturmak Için EdmGen. exe ' yi kullanın.

- Mevcut bir modeli doğrulayın. Daha fazla bilgi için [nasıl yapılır: Modeli ve eşleme dosyalarını](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)doğrulamak Için EdmGen. exe ' yi kullanın.

- Kavramsal model C# (. csdl) dosyasından oluşturulan nesne sınıflarını içeren bir veya Visual Basic kodu dosyası oluşturun. Daha fazla bilgi için [nasıl yapılır: Nesne katmanı kodu](how-to-use-edmgen-exe-to-generate-object-layer-code.md)oluşturmak Için EdmGen. exe ' yi kullanın.

- Mevcut bir C# model için önceden oluşturulmuş görünümleri içeren bir veya Visual Basic kodu dosyası oluşturun. Daha fazla bilgi için [şunları yapın: Sorgu performansını](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))artırmak Için görünümleri önceden oluşturun.

EdmGen. exe aracı .NET Framework dizinine yüklenir. Çoğu durumda, bu C:\windows\Microsoft.NET\Framework\v4.0. içinde bulunur 64 bit sistemler için bu C:\windows\Microsoft.NET\Framework64\v4.0. konumunda bulunur Ayrıca, EdmGen. exe aracına Visual Studio komut isteminden erişebilirsiniz ( **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin, Microsoft Visual Studio Visual Studio Araçları **2010**' nin üzerine gelinve ardından **Visual Studio 2010 ' ye tıklayabilirsiniz. Komut Istemi**).

## <a name="syntax"></a>Sözdizimi

```
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Mod

EdmGen. exe aracını kullanırken aşağıdaki modlardan birini belirtmeniz gerekir.

|Mod|Açıklama|
|----------|-----------------|
|`/mode:ValidateArtifacts`|. Csdl,. ssdl ve. MSL dosyalarını doğrular ve hataları ya da uyarıları görüntüler.<br /><br /> Bu seçenek `/inssdl` veya `/incsdl` bağımsız değişkenlerden en az birini gerektirir. `/inmsl` Belirtilmişse vebağımsız`/incsdl`değişkenlerdegereklidir. `/inssdl`|
|`/mode:FullGeneration`|`/connectionstring` Seçeneğinde belirtilen veritabanı bağlantı bilgilerini kullanır ve. csdl,. ssdl,. MSL, nesne katmanı ve görünüm dosyalarını oluşturur.<br /><br /> Bu seçenek, bir `/connectionstring` bağımsız değişken ve bir `/project` `/outmsdl` `/outcsdl` `/outssdl` `/entitycontainer` bağımsız değişken ya`/namespace`da,,,,, ve bağımsız değişken gerektirir. `/outobjectlayer` `/outviews`|
|`/mode:FromSSDLGeneration`|Belirtilen. ssdl dosyasından. csdl ve. MSL dosyalarını, kaynak kodunu ve görünümleri oluşturur.<br /><br /> Bu seçenek `/inssdl` bağımsız değişkeni ve `/outmsl`bir `/project` `/outcsdl`bağımsızdeğişkeni ya`/namespace,` da,`/entitycontainer` ,, ve bağımsız değişkenlerini gerektirir. `/outobjectlayer` `/outviews`|
|`/mode:EntityClassGeneration`|. Csdl dosyasından oluşturulan sınıfları içeren bir kaynak kodu dosyası oluşturur.<br /><br /> Bu seçenek bağımsız değişkeni `/incsdl` ve bağımsız değişkeni ya `/project` `/outobjectlayer` da bağımsız değişkenini gerektirir. `/language` Bağımsız değişken isteğe bağlıdır.|
|`/mode:ViewGeneration`|. Csdl,. ssdl ve. msl dosyalarından oluşturulan görünümleri içeren bir kaynak kodu dosyası oluşturur.<br /><br /> Bu seçenek,, `/inssdl` `/inmsl,` ve `/incsdl` yada`/outviews`bağımsızdeğişkenlerinigerektirir. `/project` `/language` Bağımsız değişken isteğe bağlıdır.|

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|`/p[roject]:`\<dize >|Kullanılacak projenin adını belirtir. Proje adı, ad alanı ayarı için varsayılan olarak, model ve eşleme dosyalarının adı, nesne kaynak dosyasının adı ve görünüm oluşturma kaynak dosyasının adı olarak kullanılır. Varlık kapsayıcı adı, Project > bağlamı \<olarak ayarlanır.|
|`/prov[ider]:`\<dize >|Depolama modeli (. ssdl) dosyasını oluşturmak için kullanılacak .NET Framework veri sağlayıcısının adı. Varsayılan sağlayıcı, SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) için .NET Framework veri sağlayıcısı.|
|`/c[onnectionstring]:`\<bağlantı dizesi >|Veri kaynağına bağlanmak için kullanılan dizeyi belirtir.|
|`/incsdl:`\<Dosya >|. Csdl dosyasını veya. csdl dosyalarının bulunduğu bir dizini belirtir. Birkaç dizin veya. csdl dosyası belirleyebilmeniz için, bu bağımsız değişken birden çok kez belirtilebilir. Birden çok dizin belirtilmesi, kavramsal model birçok Dosya arasında`/mode:EntityClassGeneration`bölündüğünde sınıfları (`/mode:ViewGeneration`) veya görünümleri () oluşturmak için yararlı olabilir. Bu, birden çok modeli (`/mode:ValidateArtifacts`) doğrulamak istediğinizde de yararlı olabilir.|
|`/refcsdl:`\<Dosya >|Kaynak. csdl dosyasındaki başvuruları çözümlemek için kullanılan ek. csdl dosyasını veya dosyalarını belirtir. (Kaynak. csdl dosyası, `/incsdl` seçeneği tarafından belirtilen dosyadır). `/refcsdl` Dosya, kaynak. csdl dosyasının bağlı olduğu türleri içerir. Bu bağımsız değişken birden çok kez belirtilebilir.|
|`/inmsl:`\<Dosya >|. Msl dosyasını veya. msl dosyalarının bulunduğu bir dizini belirtir. Birkaç dizin veya. msl dosyası belirleyebilmeniz için bu bağımsız değişken birden çok kez belirtilebilir. Birden çok dizin belirtilmesi, kavramsal model birçok Dosya arasında`/mode:ViewGeneration`bölündüğünde görünümler () oluşturmak için yararlı olabilir. Bu, birden çok modeli (`/mode:ValidateArtifacts`) doğrulamak istediğinizde de yararlı olabilir.|
|`/inssdl:`\<Dosya >|. Ssdl dosyasını veya. ssdl dosyasının bulunduğu bir dizini belirtir. Birkaç dizin veya. ssdl dosyası belirleyebilmeniz için bu bağımsız değişken birden çok kez belirtilebilir. Bu, birden çok modeli `(/mode:ValidateArtifacts)`doğrulamak istediğinizde yararlı olabilir.|
|`/outcsdl:`\<Dosya >|Oluşturulacak. csdl dosyasının adını belirtir.|
|`/outmsl:`\<Dosya >|Oluşturulacak. msl dosyasının adını belirtir.|
|`/outssdl:`\<Dosya >|Oluşturulacak. ssdl dosyasının adını belirtir.|
|`/outobjectlayer:`\<Dosya >|. Csdl dosyasından oluşturulan nesneleri içeren kaynak kodu dosyasının adını belirtir.|
|`/outviews:`\<Dosya >|Oluşturulan görünümleri içeren kaynak kodu dosyasının adını belirtir.|
|`/language:`[VB&#124;CSharp]|Oluşturulan kaynak kodu dosyalarının dilini belirtir. Dil varsayılan olarak C#olur.|
|`/namespace:`\<dize >|Kullanılacak model ad alanını belirtir. `/mode:FullGeneration` Veya`/mode:FromSSDLGeneration`çalıştırılırken ad alanı. csdl dosyasında ayarlanır. Ad alanı çalıştırılırken `/mode:EntityClassGeneration`kullanılmaz.|
|`/entitycontainer:`\<dize >|Oluşturulan model ve eşleme dosyalarındaki `<EntityContainer>` öğeye uygulanacak adı belirtir.|
|`/pl[uralize]`|Kavramsal modeldeki `Entity`, ve adlarına ve adlara yönelik olarak, `EntitySet`, ve `NavigationProperty` adları için İngilizce-dil kuralları uygular. Bu seçenek aşağıdaki eylemleri gerçekleştirir:<br /><br /> -Tüm `EntityType` adları tekil yapın.<br />-Tüm `EntitySet` adları plural yapın.<br />-En çok `NavigationProperty` bir varlık döndüren her bir için, adı tekil yapın.<br />-Birden fazla `NavigationProperty` varlık döndüren her bir için, adı plural yapın.|
|`/SuppressForeignKeyProperties or /nofk`|Yabancı anahtar sütunlarının, kavramsal modeldeki varlık türlerinde skaler özellikler olarak gösterilmesini engeller.|
|`/help` veya `?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/nologo`|Telif hakkı iletisinin görüntülenmesini önler.|
|`/targetversion:`\<dize >|Oluşturulan kodu derlemek için kullanılacak .NET Framework sürümü. Desteklenen sürümler 4 ve 4,5 ' dir. Varsayılan değer 4 ' dir.|

## <a name="in-this-section"></a>Bu Bölümde

[Nasıl yapılır: Modeli ve eşleme dosyalarını oluşturmak için EdmGen. exe kullanma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Nasıl yapılır: Nesne katmanı kodu oluşturmak için EdmGen. exe kullanma](how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Nasıl yapılır: Dosya modeli ve eşleme dosyalarını doğrulamak için EdmGen. exe kullanma](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Varlık Veri Modeli](../entity-data-model.md)
- [CSDL, SSDL ve MSL Belirtimleri](./language-reference/csdl-ssdl-and-msl-specifications.md)
