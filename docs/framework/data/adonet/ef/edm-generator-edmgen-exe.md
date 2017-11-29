---
title: "EDM Oluşturucu (EdmGen.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe8297a1-1fc3-48ce-8eeb-f70f63f857aa
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: da99c43d9142ee754b2b48db45ca070d1ab7c4e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="edm-generator-edmgenexe"></a>EDM Oluşturucu (EdmGen.exe)
EdmGen.exe ile çalışmak için kullanılan bir komut satırı aracıdır [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] model ve dosyaları eşleme. Aşağıdakileri yapmak için EdmGen.exe Aracı'nı kullanabilirsiniz:  
  
-   Bir veri kaynağı – özel .NET Framework veri sağlayıcısı kullanarak bir veri kaynağına bağlanır ve kavramsal model (.csdl), depolama modelindeki (.ssdl) ve tarafından kullanılan eşleme (.msl) dosyalarını oluşturmak [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Daha fazla bilgi için bkz: [nasıl yapılır: dosya eşleme ve Model oluşturmak için kullanım EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
-   Var olan bir model doğrulayın. Daha fazla bilgi için bkz: [nasıl yapılır: kullanım EdmGen.exe modeli doğrulamak ve eşleme dosyalara](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md).  
  
-   Bir C# veya bir kavramsal model (.csdl) dosyasından oluşturulan nesne sınıfları içeren Visual Basic kod dosyası oluşturun. Daha fazla bilgi için bkz: [nasıl yapılır: nesne katman kodu oluşturmak için kullanım EdmGen.exe](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md).  
  
-   Var olan bir model için önceden üretilmiş görünümleri içeren bir C# veya Visual Basic kod dosyası oluşturur. Daha fazla bilgi için [nasıl yapılır: sorgu performansını artırmak için Pre-Generate görünümleri](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579).  
  
 EdmGen.exe aracına [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] dizin. Çoğu durumda bu C:\windows\Microsoft.NET\Framework\v4.0 içinde bulunur. 64 bit sistemler için bu C:\windows\Microsoft.NET\Framework64\v4.0 içinde bulunur. Visual Studio komut isteminden EdmGen.exe aracı da erişebilirsiniz (tıklatın **Başlat**, işaret **tüm programlar**, işaret **Microsoft Visual Studio 2010**, üzerine gelin **Visual Studio Araçları**ve ardından **Visual Studio 2010 Komut İstemi**).  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
EdmGen /mode:choice [options]  
```  
  
## <a name="mode"></a>Mod  
 EdmGen.exe aracı kullanırken aşağıdaki modlarından birini belirtmeniz gerekir.  
  
|Mod|Açıklama|  
|----------|-----------------|  
|`/mode:ValidateArtifacts`|.Csdl, .ssdl ve .msl dosyalarını doğrular ve herhangi bir hata veya uyarı görüntüler.<br /><br /> Bu seçenek en az birini gerektirir `/inssdl` veya `/incsdl` bağımsız değişkenler. Varsa `/inmsl` belirtilirse, `/inssdl` ve `/incsdl` bağımsız değişkenleri gereklidir de.|  
|`/mode:FullGeneration`|Belirtilen veritabanı bağlantısı bilgilerini kullanan `/connectionstring` nesne katmanı seçeneği ve .csdl, .ssdl, .msl, oluşturur ve dosyaları görüntüleyebilir.<br /><br /> Bu seçenek gerektirir bir `/connectionstring` bağımsız değişkeni ve ya da bir `/project` bağımsız değişken veya `/outssdl`, `/outcsdl`, `/outmsdl`, `/outobjectlayer`, `/outviews`, `/namespace`, ve `/entitycontainer` bağımsız değişkenler.|  
|`/mode:FromSSDLGeneration`|.CSDL ve .msl dosyalarını, kaynak kod ve görünümlerde belirtilen .ssdl dosyasından oluşturur.<br /><br /> Bu seçenek gerektirir `/inssdl` bağımsız değişkeni ve ya da bir `/project` bağımsız değişken veya `/outcsdl`, `/outmsl`, `/outobjectlayer`, `/outviews`, `/namespace,` ve `/entitycontainer` bağımsız değişkenler.|  
|`/mode:EntityClassGeneration`|.Csdl dosyasından oluşturulan sınıflar içeren bir kaynak kod dosyası oluşturur.<br /><br /> Bu seçenek gerektirir `/incsdl` bağımsız değişkeni ve ya da `/project` bağımsız değişken veya `/outobjectlayer` bağımsız değişkeni. `/language` Bağımsız değişken isteğe bağlıdır.|  
|`/mode:ViewGeneration`|.Csdl, .ssdl ve .msl dosyalarından oluşturulan görünümleri içeren bir kaynak kod dosyası oluşturur.<br /><br /> Bu seçenek gerektirir `/inssdl`, `/incsdl`, `/inmsl,` ve her iki `/project` veya `/outviews` bağımsız değişkenler. `/language` Bağımsız değişken isteğe bağlıdır.|  
  
## <a name="options"></a>Seçenekler  
  
|Seçenek|Açıklama|  
|------------|-----------------|  
|`/p[roject]:`\<dize >|Kullanmak için proje adı belirtir. Proje adı varsayılan olarak ayarlama, model ve eşleme dosyaları, nesne kaynak dosyasının adını ve görünümü nesil kaynak dosyasının adı adını ad alanı için kullanılır. Kapsayıcı adı ayarlamak \<Proje > bağlamı.|  
|`/prov[ider]:`\<dize >|Adını [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] depolama modeli (.ssdl) dosyası oluşturmak için kullanılacak veri sağlayıcısı. Varsayılan sağlayıcı [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] için SQL Server veri sağlayıcısı (<xref:System.Data.SqlClient?displayProperty=nameWithType>).|  
|`/c[onnectionstring]:`\<bağlantı dizesi >|Veri kaynağına bağlanmak için kullanılan dizeyi belirtir.|  
|`/incsdl:`\<Dosya >|.Csdl dosya veya .csdl dosyalarının bulunduğu dizin belirtir. Birkaç dizinleri veya .csdl dosyaları belirtmek için bu bağımsız değişken birden çok kez belirtilebilir. Birden çok dizin belirten sınıflar oluşturmak için kullanışlı olabilir (`/mode:EntityClassGeneration`) veya görünümler (`/mode:ViewGeneration`) ne zaman kavramsal model bölünür birkaç dosyalardaki. Birden fazla modeli doğrulamak istediğiniz zaman da yararlı olabilir (`/mode:ValidateArtifacts`).|  
|`/refcsdl:`\<Dosya >|Ek .csdl dosya veya kaynak .csdl dosyadaki tüm başvuruları çözümlemek için kullanılan dosyaları belirtir. (Kaynak .csdl dosyası değil, tarafından belirtilen dosya `/incsdl` seçeneği). `/refcsdl` Dosyası kaynak .csdl dosya bağlıdır türleri içerir. Bu bağımsız değişken birden çok kez belirtilebilir.|  
|`/inmsl:`\<Dosya >|.Msl dosya veya .msl dosyalarının bulunduğu dizin belirtir. Birkaç dizinleri veya .msl dosyaları belirtmek için bu bağımsız değişken birden çok kez belirtilebilir. Birden çok dizin belirtme görünümleri oluşturmak için kullanışlı olabilir (`/mode:ViewGeneration`) ne zaman kavramsal model bölünür birkaç dosyalardaki. Birden fazla modeli doğrulamak istediğiniz zaman da yararlı olabilir (`/mode:ValidateArtifacts`).|  
|`/inssdl:`\<Dosya >|.Ssdl dosya veya .ssdl dosyasının bulunduğu dizini belirtir. Birkaç dizinleri veya .ssdl dosyaları belirtmek için bu bağımsız değişken birden çok kez belirtilebilir. Birden fazla modeli doğrulamak istediğiniz durumlarda bu kullanışlı olabilir `(/mode:ValidateArtifacts)`.|  
|`/outcsdl:`\<Dosya >|Oluşturulacak .csdl dosya adını belirtir.|  
|`/outmsl:`\<Dosya >|Oluşturulacak .msl dosya adını belirtir.|  
|`/outssdl:`\<Dosya >|Oluşturulacak .ssdl dosya adını belirtir.|  
|`/outobjectlayer:`\<Dosya >|.Csdl dosyasından oluşturulan nesneleri içeren kaynak kodu dosyasının adını belirtir.|  
|`/outviews:`\<Dosya >|Oluşturulan görünümleri içeren kaynak kodu dosyasının adını belirtir.|  
|`/language:`[VB &#124; CSharp]|Oluşturulan kaynak kodu dosyaları dilini belirtir. C# dil Varsayılanları.|  
|`/namespace:`\<dize >|Kullanılacak model ad belirtir. Ad alanı .csdl dosyasında çalıştırırken ayarlandığından `/mode:FullGeneration` veya `/mode:FromSSDLGeneration`. Ad alanı çalıştırırken kullanılmayan `/mode:EntityClassGeneration`.|  
|`/entitycontainer:`\<dize >|Uygulamak için adını belirtir `<EntityContainer>` eşleme dosyaları ve oluşturulmuş bir model öğesi.|  
|`/pl[uralize]`|Singulars ve çoğul ekleri için İngilizce kuralları uygular `Entity`, `EntitySet`, ve `NavigationProperty` kavramsal modelde adları. Bu seçenek, aşağıdaki eylemleri gerçekleştirir:<br /><br /> -Tüm olun `EntityType` tekil adları.<br />-Tüm olun `EntitySet` adlarını çoğul.<br />-İçin her `NavigationProperty` en çok bir varlık döndüren, adı tekil yapın.<br />-İçin her `NavigationProperty` birden fazla varlık döndüren, adı çoğul olun.|  
|`/SupressForeignKeyProperties or /nofk`|Yabancı anahtar sütunları, kavramsal modeldeki varlık türlerinde skaler özellik olarak sunulan engeller.|  
|`/help`veya`?`|Araç için komut sözdizimini ve seçenekleri görüntüler.|  
|`/nologo`|Telif Hakkı görüntüleme iletiden gizler.|  
|`/targetversion:`\<dize >|Oluşturulan kod derlemek için kullanılan .NET Framework sürümü. Desteklenen sürümler 4 ve 4. 5 ' dir. Varsayılan olarak 4.|  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: EdmGen.exe modeli ve eşleme dosyaları oluşturmak için kullanın](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)  
  
 [Nasıl yapılır: nesne katmanı kodu oluşturmak için EdmGen.exe kullanın](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)  
  
 [Nasıl yapılır: EdmGen.exe modeli ve eşleme dosyaları doğrulamak için kullanın](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET varlık veri modeli araçları](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [Varlık veri modeli](../../../../../docs/framework/data/adonet/entity-data-model.md)  
 [CSDL, SSDL ve MSL belirtimleri](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
