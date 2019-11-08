---
title: EDM Oluşturucu (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: 858525a81e7779e7631ee8ac959110ba946cf652
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738524"
---
# <a name="edm-generator-edmgenexe"></a>EDM Oluşturucu (EdmGen.exe)

EdmGen. exe, Entity Framework modeli ve eşleme dosyalarıyla çalışmak için kullanılan bir komut satırı aracıdır. EdmGen. exe aracını kullanarak şunları gerçekleştirebilirsiniz:

- Veri kaynağına özgü .NET Framework veri sağlayıcısı kullanarak bir veri kaynağına bağlanın ve Entity Framework tarafından kullanılan kavramsal model (. csdl), depolama modeli (. ssdl) ve eşleme (. MSL) dosyalarını oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: EdmGen. exe kullanarak model ve eşleme dosyaları oluşturma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

- Mevcut bir modeli doğrulayın. Daha fazla bilgi için bkz. [nasıl yapılır: EdmGen. exe kullanarak model ve eşleme dosyalarını doğrulama](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).

- Kavramsal model C# (. csdl) dosyasından oluşturulan nesne sınıflarını içeren bir veya Visual Basic kodu dosyası oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: EdmGen. exe kullanarak nesne katmanı kodu oluşturma](how-to-use-edmgen-exe-to-generate-object-layer-code.md).

- Mevcut bir C# model için önceden oluşturulmuş görünümleri içeren bir veya Visual Basic kodu dosyası oluşturun. Daha fazla bilgi için, bkz. [sorgu performansını artırmak Için görünümleri önceden oluşturma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).

EdmGen. exe aracı .NET Framework dizinine yüklenir. Çoğu durumda, bu C:\windows\Microsoft.NET\Framework\v4.0. içinde bulunur 64 bit sistemler için bu C:\windows\Microsoft.NET\Framework64\v4.0. konumunda bulunur Ayrıca, EdmGen. exe aracına Visual Studio komut isteminden erişebilirsiniz ( **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin, Microsoft Visual Studio Visual Studio Araçları **2010**' nin üzerine gelinve ardından **Visual Studio 2010 ' ye tıklayabilirsiniz. Komut Istemi**).

## <a name="syntax"></a>Sözdizimi

```console
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Mod

EdmGen. exe aracını kullanırken aşağıdaki modlardan birini belirtmeniz gerekir.

|Mod|Açıklama|
|----------|-----------------|
|`/mode:ValidateArtifacts`|. Csdl,. ssdl ve. MSL dosyalarını doğrular ve hataları ya da uyarıları görüntüler.<br /><br /> Bu seçenek `/inssdl` veya `/incsdl` bağımsız değişkenlerinden en az birini gerektirir. `/inmsl` belirtilirse, `/inssdl` ve `/incsdl` bağımsız değişkenleri de gereklidir.|
|`/mode:FullGeneration`|`/connectionstring` seçeneğinde belirtilen veritabanı bağlantı bilgilerini kullanır ve. csdl,. ssdl,. MSL, nesne katmanı ve görünüm dosyalarını oluşturur.<br /><br /> Bu seçenek `/connectionstring` bir bağımsız değişkeni ve bir `/project` bağımsız değişkeni ya da `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace`ve `/entitycontainer` bağımsız değişkenlerini gerektirir.|
|`/mode:FromSSDLGeneration`|Belirtilen. ssdl dosyasından. csdl ve. MSL dosyalarını, kaynak kodunu ve görünümleri oluşturur.<br /><br /> Bu seçenek `/inssdl` bağımsız değişkeni ve bir `/project` bağımsız değişkeni ya da `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` ve `/entitycontainer` bağımsız değişkenlerini gerektirir.|
|`/mode:EntityClassGeneration`|. Csdl dosyasından oluşturulan sınıfları içeren bir kaynak kodu dosyası oluşturur.<br /><br /> Bu seçenek `/incsdl` bağımsız değişkenini ve `/project` bağımsız değişkenini ya da `/outobjectlayer` bağımsız değişkenini gerektirir. `/language` bağımsız değişkeni isteğe bağlıdır.|
|`/mode:ViewGeneration`|. Csdl,. ssdl ve. msl dosyalarından oluşturulan görünümleri içeren bir kaynak kodu dosyası oluşturur.<br /><br /> Bu seçenek `/inssdl`, `/incsdl`, `/inmsl,` ve `/project` ya da `/outviews` bağımsız değişkenlerini gerektirir. `/language` bağımsız değişkeni isteğe bağlıdır.|

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|`/p[roject]:`\<dize >|Kullanılacak projenin adını belirtir. Proje adı, ad alanı ayarı için varsayılan olarak, model ve eşleme dosyalarının adı, nesne kaynak dosyasının adı ve görünüm oluşturma kaynak dosyasının adı olarak kullanılır. Varlık kapsayıcı adı \<Proje > bağlamı olarak ayarlanır.|
|`/prov[ider]:`\<dize >|Depolama modeli (. ssdl) dosyasını oluşturmak için kullanılacak .NET Framework veri sağlayıcısının adı. Varsayılan sağlayıcı SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) için .NET Framework Veri Sağlayıcısı.|
|`/c[onnectionstring]:`\<bağlantı dizesi >|Veri kaynağına bağlanmak için kullanılan dizeyi belirtir.|
|`/incsdl:`\<Dosya >|. Csdl dosyasını veya. csdl dosyalarının bulunduğu bir dizini belirtir. Birkaç dizin veya. csdl dosyası belirleyebilmeniz için, bu bağımsız değişken birden çok kez belirtilebilir. Birden çok dizin belirtilmesi, kavramsal model birçok Dosya arasında bölündüğünde sınıfları (`/mode:EntityClassGeneration`) veya görünümleri (`/mode:ViewGeneration`) oluşturmak için yararlı olabilir. Bu, birden çok modeli (`/mode:ValidateArtifacts`) doğrulamak istediğinizde de yararlı olabilir.|
|`/refcsdl:`\<Dosya >|Kaynak. csdl dosyasındaki başvuruları çözümlemek için kullanılan ek. csdl dosyasını veya dosyalarını belirtir. (Kaynak. csdl dosyası, `/incsdl` seçeneği tarafından belirtilen dosyadır). `/refcsdl` dosyası, kaynak. csdl dosyasının bağlı olduğu türleri içerir. Bu bağımsız değişken birden çok kez belirtilebilir.|
|`/inmsl:`\<Dosya >|. Msl dosyasını veya. msl dosyalarının bulunduğu bir dizini belirtir. Birkaç dizin veya. msl dosyası belirleyebilmeniz için bu bağımsız değişken birden çok kez belirtilebilir. Birden çok dizin belirtilmesi, kavramsal model çeşitli dosyalara bölündüğünde görünümler oluşturmak için yararlı olabilir (`/mode:ViewGeneration`). Bu, birden çok modeli (`/mode:ValidateArtifacts`) doğrulamak istediğinizde de yararlı olabilir.|
|`/inssdl:`\<Dosya >|. Ssdl dosyasını veya. ssdl dosyasının bulunduğu bir dizini belirtir. Birkaç dizin veya. ssdl dosyası belirleyebilmeniz için bu bağımsız değişken birden çok kez belirtilebilir. Bu, birden çok modeli `(/mode:ValidateArtifacts)`doğrulamak istediğinizde yararlı olabilir.|
|`/outcsdl:`\<Dosya >|Oluşturulacak. csdl dosyasının adını belirtir.|
|`/outmsl:`\<Dosya >|Oluşturulacak. msl dosyasının adını belirtir.|
|`/outssdl:`\<Dosya >|Oluşturulacak. ssdl dosyasının adını belirtir.|
|`/outobjectlayer:`\<Dosya >|. Csdl dosyasından oluşturulan nesneleri içeren kaynak kodu dosyasının adını belirtir.|
|`/outviews:`\<Dosya >|Oluşturulan görünümleri içeren kaynak kodu dosyasının adını belirtir.|
|`/language:`[VB&#124;CSharp]|Oluşturulan kaynak kodu dosyalarının dilini belirtir. Dil varsayılan olarak C#olur.|
|`/namespace:`\<dize >|Kullanılacak model ad alanını belirtir. Ad alanı, `/mode:FullGeneration` veya `/mode:FromSSDLGeneration`çalıştırılırken. csdl dosyasında ayarlanır. `/mode:EntityClassGeneration`çalıştırılırken ad alanı kullanılmaz.|
|`/entitycontainer:`\<dize >|Oluşturulan model ve eşleme dosyalarındaki `<EntityContainer>` öğesi için uygulanacak adı belirtir.|
|`/pl[uralize]`|Kavramsal modeldeki `Entity`, `EntitySet`ve `NavigationProperty` adlarına ve çoğul ve plurlar için Ingilizce-dil kuralları uygular. Bu seçenek aşağıdaki eylemleri gerçekleştirir:<br /><br /> -Tüm `EntityType` adlarını tekil yapın.<br />-Tüm `EntitySet` adları plural yapın.<br />-En çok bir varlık döndüren her `NavigationProperty` için, adı tekil yapın.<br />-Birden fazla varlık döndüren her `NavigationProperty` için, adı plural yapın.|
|`/SuppressForeignKeyProperties or /nofk`|Yabancı anahtar sütunlarının, kavramsal modeldeki varlık türlerinde skaler özellikler olarak gösterilmesini engeller.|
|`/help` veya `?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/nologo`|Telif hakkı iletisinin görüntülenmesini önler.|
|`/targetversion:` \<dize >|Oluşturulan kodu derlemek için kullanılacak .NET Framework sürümü. Desteklenen sürümler 4 ve 4,5 ' dir. Varsayılan değer 4 ' dir.|

## <a name="in-this-section"></a>Bu Bölümde

[Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma](how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyalarını Doğrulama](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Varlık Veri Modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Varlık Veri Modeli](../entity-data-model.md)
- [CSDL, SSDL ve MSL Belirtimleri](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
