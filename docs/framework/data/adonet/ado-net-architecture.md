---
title: ADO.NET Mimarisi
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: 0e6f80051c00b23f76495477f713427f2b93019c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932249"
---
# <a name="adonet-architecture"></a>ADO.NET Mimarisi
Veri işleme, temelde genellikle bağlantı tabanlı, iki katmanlı bir modele bağlıdır. Veri işleme giderek çok katmanlı mimarilerin kullanıldığı için programcılar, uygulamaları için daha iyi ölçeklenebilirlik sağlamak üzere bağlantısı kesilen bir yaklaşıma geçiş yapıyor.  
  
## <a name="adonet-components"></a>ADO.NET bileşenleri  
 Verilere erişmek ve veri işlemek için ADO.NET 'in iki ana bileşeni .NET Framework veri sağlayıcılarıdır ve ' <xref:System.Data.DataSet>dir.  
  
### <a name="net-framework-data-providers"></a>.NET Framework Veri Sağlayıcıları  
 .NET Framework veri sağlayıcıları doğrudan veri işleme ve hızlı, salt iletme, verilere salt okuma erişimi için tasarlanmış bileşenlerdir. `Connection` Nesnesi bir veri kaynağına bağlantı sağlar. `Command` Nesnesi, veri döndürmek, verileri değiştirmek, saklı yordamları çalıştırmak ve parametre bilgilerini göndermek veya almak için veritabanı komutlarına erişim sağlar. , `DataReader` Veri kaynağından yüksek performanslı veri akışı sağlar. Son olarak, `DataSet` nesnesi ve veri kaynağı arasında köprü sağlar.`DataAdapter` , `DataAdapter` Veri `Command` kaynağındakiSQL`DataSet` komutlarını yürütmek için nesneleri kullanır ve verileri veri kaynağına geri yüklemek veiçindekiverilerdeyapılandeğişikliklerimutabıkkılmakiçinkullanır.`DataSet` Daha fazla bilgi için bkz. [veri sağlayıcıları .NET Framework](../../../../docs/framework/data/adonet/data-providers.md) ve [verileri alma ve değiştirme ADO.net](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Veri kümesi  
 ADO.net `DataSet` , herhangi bir veri kaynağından bağımsız olarak veri erişimi için özel olarak tasarlanmıştır. Sonuç olarak, birden çok ve farklı veri kaynaklarıyla birlikte kullanılabilir, XML verileriyle birlikte kullanılabilir veya uygulamada yerel verileri yönetmek için kullanılır. , `DataSet` Veri satırlarından ve sütunlarından oluşan bir veya <xref:System.Data.DataTable> daha fazla nesnenin koleksiyonunu ve ayrıca birincil anahtar, yabancı anahtar, kısıtlama ve `DataTable` nesnelerdeki verilerle ilgili ilişki bilgilerini içerir. Daha fazla bilgi için bkz. [veri kümeleri, DataTable ve DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Aşağıdaki diyagramda bir .NET Framework veri sağlayıcısı ve ile `DataSet`arasındaki ilişki gösterilmektedir.  
  
 ![ADO.net grafiği](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
ADO.NET mimarisi  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>DataReader veya veri kümesi seçme  
 Uygulamanızın bir `DataReader` ( [DataReader kullanarak veri alma](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) veya bir `DataSet` (bkz. veri [kümeleri, DataTable ve DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)) kullanması gerektiğine karar verirken, uygulamanızın gerektirdiği işlev türünü göz önünde bulundurun. Şunları yapmak `DataSet` için bir kullanın:  
  
- Verileri işleyebilmeniz için uygulamanızdaki yerel olarak önbelleğe alma. Yalnızca bir sorgunun `DataReader` sonuçlarını okumanız gerekiyorsa, daha iyi bir seçenektir.  
  
- Katmanlar arasında veya bir XML Web hizmetinden uzak veriler.  
  
- Windows Forms denetimine bağlama veya birden fazla kaynaktaki verileri birleştirme ve ilişkilendirme gibi verilerle dinamik olarak etkileşime geçin.  
  
- Veri kaynağına açık bir bağlantı gerektirmeden veri üzerinde kapsamlı işlem gerçekleştirerek, bağlantıyı diğer istemciler tarafından kullanılmak üzere serbest bırakır.  
  
 Tarafından `DataSet`sağlanmış işlevselliğe ihtiyacınız yoksa, verilerinizi yalnızca ileri, Salt okunabilir bir şekilde döndürmek `DataReader` için kullanarak uygulamanızın performansını artırabilirsiniz. , `DataAdapter` Öğesininiçeriğini`DataSet` doldurmak `DataReader` [](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)için (bkz. DataAdapter 'tan bir veri kümesini doldurma) kullanmasına karşın, kullanarak, bu, `DataReader` ve içeriğinin oluşturulması ve doldurulması için gereken işlemden kaçının. `DataSet` `DataSet`  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 LINQ to DataSet, veri kümesi nesnesinde önbelleğe alınan veriler üzerinde sorgu özellikleri ve derleme zamanı tür denetimi sağlar. Sorgular, C# veya Visual Basic gibi .NET Framework geliştirme dilinden birine yazmanızı sağlar. Daha fazla bilgi için [LINQ to DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 LINQ to SQL, bir ara kavramsal model kullanılmadan ilişkisel bir veritabanının veri yapılarına eşlenmiş bir nesne modeline karşı sorguları destekler. Her tablo ayrı bir sınıf tarafından temsil edilir ve nesne modelini ilişkisel veritabanı şemasına sıkı bir şekilde ayırır. LINQ to SQL, nesne modelindeki dil ile tümleşik sorguları Transact-SQL ' e çevirir ve yürütmek üzere veritabanına gönderir. Veritabanı sonuçları döndürdüğünde LINQ to SQL sonuçları nesnelere geri çevirir. Daha fazla bilgi için bkz. [LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 ADO.NET Entity Framework, geliştiricilerin doğrudan ilişkisel bir depolama şemasına karşı programlama yerine kavramsal bir uygulama modeline karşı programlama yaparak veri erişimi uygulamaları oluşturmalarına olanak tanımak üzere tasarlanmıştır. Amaç, veri odaklı uygulamalar için gereken kod ve bakım miktarını azaltmaktır. Daha fazla bilgi için bkz. [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
## <a name="wcf-data-services"></a>WCF Veri Hizmetleri  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Web veya intranette veri hizmetlerini dağıtmak için kullanılır. Veriler, Varlık Veri Modeli belirtimlerine göre varlıklar ve ilişkiler olarak yapılandırılır. Bu modelde dağıtılan verilere standart HTTP protokolü tarafından adreslenebilir. Daha fazla bilgi için [WCF Veri Hizmetleri 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML ve ADO.NET  
 ADO.NET, verilere bağlantısız erişim sağlamak için XML 'nin gücünden yararlanır. ADO.NET, .NET Framework içindeki XML sınıflarıyla birlikte tasarlanmıştır; her ikisi de tek bir mimarinin bileşenleridir.  
  
 ADO.net ve .NET Framework XML sınıfları `DataSet` nesnesine yakınlardır. , `DataSet` Bir XML kaynağından alınan verilerle doldurulabilir ve bunun bir dosya veya XML akışı olması olabilir. , İçindeki verilerin kaynağına bakılmaksızın şemasını xml şeması tanım dili (xsd) şeması olarak içeren World Wide Web Consortium (W3C) uyumlu XML olarak yazılabilir. `DataSet` `DataSet` XML 'nin yerel seri hale getirme biçimi `DataSet` nedeniyle, verileri katmanlar arasında taşımak için mükemmel bir ortamdır; bu, verileri ve şema bağlamını bir XML Web hizmetinden ve bir XML Web hizmetinden uzak hale `DataSet` getirmek için en uygun seçeneği sağlar. Daha fazla bilgi için bkz. [XML belgeleri ve verileri](../../../standard/data/xml/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
