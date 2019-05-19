---
title: ADO.NET Mimarisi
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: 13f65d0a2daf3b477a9b29c4de84fb359c946201
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877240"
---
# <a name="adonet-architecture"></a>ADO.NET Mimarisi
Geleneksel veri işleme öncelikli olarak bağlantı tabanlı, iki katmanlı modeli üzerinde yararlandı. Veri işleme, çok katmanlı mimariler giderek kullanır gibi programcılar kendi uygulamaları için daha iyi ölçeklenebilirlik sağlamak için bağlantısı kesik bir yaklaşıma geçirirsiniz.  
  
## <a name="adonet-components"></a>ADO.NET bileşenleri  
 İki ana bileşenden [!INCLUDE[ado_orcas_long](../../../../includes/ado-orcas-long-md.md)] erişme ve verileri düzenleme .NET Framework veri sağlayıcıları için ve <xref:System.Data.DataSet>.  
  
### <a name="net-framework-data-providers"></a>.NET Framework Veri Sağlayıcıları  
 .NET Framework veri sağlayıcıları açıkça veri işleme ve verileri hızlı, yalnızca iletme, salt okunur erişim için tasarlanmış bileşenlerdir. `Connection` Nesnesi, bir veri kaynağına bağlantı sağlar. `Command` Nesne verileri döndürür, verileri değiştirme, saklı yordamları çalıştırmak ve gönderme veya parametre bilgilerini almak için veritabanı komutları erişim sağlar. `DataReader` Veri kaynağından veri yüksek performanslı akışını sağlar. Son olarak, `DataAdapter` arasında köprü sağlar `DataSet` nesnesi ve veri kaynağı. `DataAdapter` Kullanan `Command` veri kaynağında hem yük SQL komutları yürütme nesnelere `DataSet` verilerle ve verilerde yapılan değişiklikleri mutabık kılma `DataSet` veri kaynağına geri. Daha fazla bilgi için [.NET Framework veri sağlayıcıları](../../../../docs/framework/data/adonet/data-providers.md) ve [alınıyor ve ADO.NET veri değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Veri kümesi  
 ADO.NET `DataSet` açıkça herhangi bir veri kaynağını bağımsız veri erişimi için tasarlanmıştır. Sonuç olarak, birden çok ile kullanılabilir ve farklı veri kaynakları, XML verileri ile kullanılan veya uygulamaya yerel verileri yönetmek için kullanılamaz. `DataSet` İçeren bir koleksiyon bir veya daha fazla <xref:System.Data.DataTable> satırları ve sütunları veri ve birincil anahtar, yabancı anahtar kısıtlaması ve ilişki hakkında bilgi verileri oluşan nesneler `DataTable` nesneleri. Daha fazla bilgi için [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Aşağıdaki diyagramda bir .NET Framework veri sağlayıcısı arasındaki ilişkiyi gösterir ve `DataSet`.  
  
 ![ADO.Net grafik](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
ADO.NET mimarisi  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>DataReader veya bir veri kümesi seçme  
 İstediğinize karar verdiğinizde, uygulamanızın kullanıp kullanmayacağını bir `DataReader` (bkz [alma verileri kullanarak bir DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) veya bir `DataSet` (bkz [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)), türünü göz önünde bulundurun uygulamanızın gerektirdiği işlevselliği. Kullanım bir `DataSet` aşağıdakileri yapmak için:  
  
- Verilerin uygulamanızda yerel olarak işlemek önbelleğe alınması. Yalnızca bir sorgunun sonuçlarını okumak gerekiyorsa `DataReader` daha iyi bir seçimdir.  
  
- Uzak veri katmanları arasında veya bir XML Web hizmeti.  
  
- Dinamik olarak bir Windows Forms denetimine bağlama veya birleştirme ve birden fazla kaynaktan veri ilgili gibi verilerle etkileşim kurun.  
  
- Kapsamlı bir işlem açık bir bağlantı diğer istemciler tarafından kullanılacak bağlantı boşaltır veri kaynağına gerek kalmadan veri gerçekleştirin.  
  
 Tarafından sağlanan işlevselliği gerekmiyorsa `DataSet`, kullanarak uygulamanızın performansını iyileştirebilir `DataReader` verilerinizi yalnızca iletme, salt okunur bir biçimde dönün. Ancak `DataAdapter` kullanır `DataReader` içeriğini doldurmak için bir `DataSet` (bkz [dataadapter'dan bir DataSet doldurma](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)), kullanarak `DataReader`, bellek kaydedecek çünkü performansı artırabilir. kullanılması tarafından `DataSet`ve oluşturup içeriğini doldurmak için gerekli olan işleme engel `DataSet`.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 LINQ to DataSet sorgu işlevleri ve derleme zamanı tür DataSet nesnesinde önbelleği alınan veriler üzerinde denetlemesini sağlar. Bir C# veya Visual Basic gibi .NET Framework geliştirme dilinin sorgular yazmaya olanak tanır. Daha fazla bilgi için [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 LINQ to SQL'de ilişkisel veritabanı veri yapıları için bir ara kavramsal model kullanmadan eşlenmiş nesne modeli sorguları destekler. Her tablo nesne modeli ilişkisel veritabanı şemasına sıkı şekilde eşlemeyi ayrı bir sınıf tarafından temsil edilir. LINQ to SQL nesne modeli dil ile tümleşik sorgu Transact-SQL'e çevirir ve yürütme için veritabanı gönderir. Veritabanı sonuçları döndürdüğünde, LINQ to SQL sonuçları nesnelerini geri çevirir. Daha fazla bilgi için [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 ADO.NET Entity Framework, doğrudan bir ilişkisel depolama şemaya karşı programlama yerine bir uygulama kavramsal modeline karşı programlama geliştiricilerin veri erişimi uygulamaları etkinleştirmek için tasarlanmıştır. Kod ve veri odaklı uygulamalar için gerekli bakım miktarını azaltmak için hedeftir. Daha fazla bilgi için [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
## <a name="wcf-data-services"></a>WCF Veri Hizmetleri  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Veri Hizmetleri Web veya intranet üzerinde dağıtmak için kullanılır. Veri varlıkları ve ilişkileri varlık veri modeli belirtimlere göre olarak yapılandırılmıştır. Bu modelde dağıtılan standart HTTP protokolü tarafından adreslenebilir verilerdir. Daha fazla bilgi için [WCF Veri Hizmetleri 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML ve ADO.NET  
 ADO.NET veri bağlantısı kesilmiş erişim sağlamak için XML gücünden yararlanır. ADO.NET tasarlanmış el yakından .NET Framework'te XML sınıflarla oluştu; her ikisi de tek bir mimari bileşenleridir.  
  
 ADO.NET ve .NET Framework XML sınıflarda yakınsama içinde `DataSet` nesne. `DataSet` Bir dosya veya bir XML akışı olup, bir XML kaynaktan gelen veriler ile doldurulabilir. `DataSet` World-Wide Web Consortium (W3C) XML Şeması Tanım Dili (XSD) şemaya, veri kaynağı ne olursa olsun, şema içerir uyumlu XML olarak yazılmış `DataSet`. Yerel seri hale getirme biçimi nedeniyle `DataSet` XML, yapmadan katmanlar arasında verileri taşımak için mükemmel bir ortamdır `DataSet` uzak veri ve şema bağlamı için bir en iyi seçim için ve XML Web hizmeti. Daha fazla bilgi için [XML belgeleri ve verileri](../../../../docs/standard/data/xml/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
