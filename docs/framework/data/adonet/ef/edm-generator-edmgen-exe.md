---
title: EDM Oluşturucu (EdmGen.exe)
ms.date: 03/30/2017
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
ms.openlocfilehash: da5b87fa76cbc8e44f6ed60b047e5a185c2aa603
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542561"
---
# <a name="edm-generator-edmgenexe"></a>EDM Oluşturucu (EdmGen.exe)

EdmGen.exe, Entity Framework modeliyle ve eşleme dosyalarıyla çalışmak için kullanılan bir komut satırı aracıdır. EdmGen.exe aracını kullanarak şunları yapabilirsiniz:

- Veri kaynağına özgü .NET Framework veri sağlayıcısı kullanarak bir veri kaynağına bağlanın ve Entity Framework tarafından kullanılan kavramsal model (. csdl), depolama modeli (. ssdl) ve eşleme (. MSL) dosyalarını oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını oluşturmak için EdmGen.exe kullanma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).

- Mevcut bir modeli doğrulayın. Daha fazla bilgi için bkz. [nasıl yapılır: model ve eşleme dosyalarını doğrulamak için EdmGen.exe kullanma](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).

- Kavramsal model (. csdl) dosyasından oluşturulan nesne sınıflarını içeren bir C# veya Visual Basic kodu dosyası oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: nesne katmanı kodu oluşturmak için EdmGen.exe kullanma](how-to-use-edmgen-exe-to-generate-object-layer-code.md).

- Mevcut bir model için önceden oluşturulmuş görünümleri içeren bir C# veya Visual Basic kodu dosyası oluşturun. Daha fazla bilgi için, bkz. [sorgu performansını artırmak Için görünümleri önceden oluşturma](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100)).

EdmGen.exe aracı .NET Framework dizinine yüklenir. Çoğu durumda, bu C:\windows\Microsoft.NET\Framework\v4.0. içinde bulunur 64 bit sistemler için bu C:\windows\Microsoft.NET\Framework64\v4.0. konumunda bulunur Ayrıca, Visual Studio komut isteminden EdmGen.exe aracına da erişebilirsiniz ( **Başlat**' a tıklayın, **tüm programlar**' ın üzerine gelin, **Microsoft Visual Studio 2010**' a gidin, **Visual Studio Araçları**' nın üzerine gelin ve ardından **Visual Studio 2010 komut istemi**' ne tıklayabilirsiniz).

## <a name="syntax"></a>Syntax

```console
EdmGen /mode:choice [options]
```

## <a name="mode"></a>Mod

EdmGen.exe aracını kullanırken aşağıdaki modlardan birini belirtmeniz gerekir.

|Mod|Description|
|----------|-----------------|
|`/mode:ValidateArtifacts`|. Csdl,. ssdl ve. MSL dosyalarını doğrular ve hataları ya da uyarıları görüntüler.<br /><br /> Bu seçenek `/inssdl` veya bağımsız değişkenlerden en az birini gerektirir `/incsdl` . `/inmsl`Belirtilmişse `/inssdl` ve `/incsdl` bağımsız değişkenler de gereklidir.|
|`/mode:FullGeneration`|Seçeneğinde belirtilen veritabanı bağlantı bilgilerini kullanır `/connectionstring` ve. csdl,. ssdl,. MSL, nesne katmanı ve görünüm dosyalarını oluşturur.<br /><br /> Bu seçenek, bir `/connectionstring` bağımsız değişken ve bir bağımsız değişken ya da,,,,, `/project` `/outssdl` `/outcsdl` `/outmsdl` `/outobjectlayer` `/outviews` `/namespace` ve `/entitycontainer` bağımsız değişken gerektirir.|
|`/mode:FromSSDLGeneration`|Belirtilen. ssdl dosyasından. csdl ve. MSL dosyalarını, kaynak kodunu ve görünümleri oluşturur.<br /><br /> Bu seçenek `/inssdl` bağımsız değişkeni ve bir bağımsız değişkeni ya da,,, `/project` `/outcsdl` `/outmsl` `/outobjectlayer` `/outviews` `/namespace,` ve `/entitycontainer` bağımsız değişkenlerini gerektirir.|
|`/mode:EntityClassGeneration`|. Csdl dosyasından oluşturulan sınıfları içeren bir kaynak kodu dosyası oluşturur.<br /><br /> Bu seçenek bağımsız değişkeni ve bağımsız değişkeni ya da bağımsız değişkenini gerektirir `/incsdl` `/project` `/outobjectlayer` . `/language`Bağımsız değişken isteğe bağlıdır.|
|`/mode:ViewGeneration`|. Csdl,. ssdl ve. msl dosyalarından oluşturulan görünümleri içeren bir kaynak kodu dosyası oluşturur.<br /><br /> Bu seçenek,, `/inssdl` `/incsdl` `/inmsl,` ve `/project` ya da `/outviews` bağımsız değişkenlerini gerektirir. `/language`Bağımsız değişken isteğe bağlıdır.|

## <a name="options"></a>Seçenekler

|Seçenek|Açıklama|
|------------|-----------------|
|`/p[roject]:`\<string>|Kullanılacak projenin adını belirtir. Proje adı, ad alanı ayarı için varsayılan olarak, model ve eşleme dosyalarının adı, nesne kaynak dosyasının adı ve görünüm oluşturma kaynak dosyasının adı olarak kullanılır. Varlık kapsayıcı adı bağlam olarak ayarlandı \<project> .|
|`/prov[ider]:`\<string>|Depolama modeli (. ssdl) dosyasını oluşturmak için kullanılacak .NET Framework veri sağlayıcısının adı. Varsayılan sağlayıcı, SQL Server () için .NET Framework Veri Sağlayıcısı <xref:System.Data.SqlClient?displayProperty=nameWithType> .|
|`/c[onnectionstring]:`\<connection string>|Veri kaynağına bağlanmak için kullanılan dizeyi belirtir.|
|`/incsdl:`\<file>|. Csdl dosyasını veya. csdl dosyalarının bulunduğu bir dizini belirtir. Birkaç dizin veya. csdl dosyası belirleyebilmeniz için, bu bağımsız değişken birden çok kez belirtilebilir. Birden çok dizin belirtilmesi `/mode:EntityClassGeneration` `/mode:ViewGeneration` , kavramsal model birçok Dosya arasında bölündüğünde sınıfları () veya görünümleri () oluşturmak için yararlı olabilir. Bu, birden çok modeli () doğrulamak istediğinizde de yararlı olabilir `/mode:ValidateArtifacts` .|
|`/refcsdl:`\<file>|Kaynak. csdl dosyasındaki başvuruları çözümlemek için kullanılan ek. csdl dosyasını veya dosyalarını belirtir. (Kaynak. csdl dosyası, seçeneği tarafından belirtilen dosyadır `/incsdl` ). `/refcsdl`Dosya, kaynak. csdl dosyasının bağlı olduğu türleri içerir. Bu bağımsız değişken birden çok kez belirtilebilir.|
|`/inmsl:`\<file>|. Msl dosyasını veya. msl dosyalarının bulunduğu bir dizini belirtir. Birkaç dizin veya. msl dosyası belirleyebilmeniz için bu bağımsız değişken birden çok kez belirtilebilir. Birden çok dizin belirtilmesi `/mode:ViewGeneration` , kavramsal model birçok Dosya arasında bölündüğünde görünümler () oluşturmak için yararlı olabilir. Bu, birden çok modeli () doğrulamak istediğinizde de yararlı olabilir `/mode:ValidateArtifacts` .|
|`/inssdl:`\<file>|. Ssdl dosyasını veya. ssdl dosyasının bulunduğu bir dizini belirtir. Birkaç dizin veya. ssdl dosyası belirleyebilmeniz için bu bağımsız değişken birden çok kez belirtilebilir. Bu, birden çok modeli doğrulamak istediğinizde yararlı olabilir `(/mode:ValidateArtifacts)` .|
|`/outcsdl:`\<file>|Oluşturulacak. csdl dosyasının adını belirtir.|
|`/outmsl:`\<file>|Oluşturulacak. msl dosyasının adını belirtir.|
|`/outssdl:`\<file>|Oluşturulacak. ssdl dosyasının adını belirtir.|
|`/outobjectlayer:`\<file>|. Csdl dosyasından oluşturulan nesneleri içeren kaynak kodu dosyasının adını belirtir.|
|`/outviews:`\<file>|Oluşturulan görünümleri içeren kaynak kodu dosyasının adını belirtir.|
|`/language:`[VB&#124;CSharp]|Oluşturulan kaynak kodu dosyalarının dilini belirtir. Dil varsayılan olarak C# ' dir.|
|`/namespace:`\<string>|Kullanılacak model ad alanını belirtir. Veya çalıştırılırken ad alanı. csdl dosyasında ayarlanır `/mode:FullGeneration` `/mode:FromSSDLGeneration` . Ad alanı çalıştırılırken kullanılmaz `/mode:EntityClassGeneration` .|
|`/entitycontainer:`\<string>|`<EntityContainer>`Oluşturulan model ve eşleme dosyalarındaki öğeye uygulanacak adı belirtir.|
|`/pl[uralize]`|`Entity` `EntitySet` Kavramsal modeldeki, ve adlarına ve adlara yönelik olarak,, ve adları için İngilizce-dil kuralları uygular `NavigationProperty` . Bu seçenek aşağıdaki eylemleri gerçekleştirir:<br /><br /> -Tüm `EntityType` adları tekil yapın.<br />-Tüm `EntitySet` adları plural yapın.<br />- `NavigationProperty` En çok bir varlık döndüren her bir için, adı tekil yapın.<br />-Birden `NavigationProperty` fazla varlık döndüren her bir için, adı plural yapın.|
|`/SuppressForeignKeyProperties or /nofk`|Yabancı anahtar sütunlarının, kavramsal modeldeki varlık türlerinde skaler özellikler olarak gösterilmesini engeller.|
|`/help` veya `?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|
|`/nologo`|Telif hakkı iletisinin görüntülenmesini önler.|
|`/targetversion:` \<string>|Oluşturulan kodu derlemek için kullanılacak .NET Framework sürümü. Desteklenen sürümler 4 ve 4,5 ' dir. Varsayılan değer 4 ' dir.|

## <a name="in-this-section"></a>Bu Bölümde

[Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyaları Oluşturma](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)

[Nasıl yapılır: EdmGen.exe kullanarak Nesne Katmanı Kodu Oluşturma](how-to-use-edmgen-exe-to-generate-object-layer-code.md)

[Nasıl yapılır: EdmGen.exe kullanarak Model ve Eşleme Dosyalarını Doğrulama](how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Varlık Veri Modeli araçları](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
- [Varlık Veri Modeli](../entity-data-model.md)
- [CSDL, SSDL ve MSL Belirtimleri](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
