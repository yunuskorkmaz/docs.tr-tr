---
title: Mimari
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: de33c9964f3c03b18593b0df0607f941d2117be0
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980320"
---
# <a name="adonet-architecture"></a>ADO.NET Mimarisi
Veri işleme, temelde genellikle bağlantı tabanlı, iki katmanlı bir modele bağlıdır. Veri işleme giderek çok katmanlı mimarilerin kullanıldığı için programcılar, uygulamaları için daha iyi ölçeklenebilirlik sağlamak üzere bağlantısı kesilen bir yaklaşıma geçiş yapıyor.  
  
## <a name="adonet-components"></a>ADO.NET bileşenleri  
 Verilere erişmek ve veri işlemek için ADO.NET 'in iki ana bileşeni .NET Framework veri sağlayıcılarıdır ve <xref:System.Data.DataSet>.  
  
### <a name="net-framework-data-providers"></a>.NET Framework Veri Sağlayıcıları  
 .NET Framework veri sağlayıcıları doğrudan veri işleme ve hızlı, salt iletme, verilere salt okuma erişimi için tasarlanmış bileşenlerdir. `Connection` nesnesi bir veri kaynağına bağlantı sağlar. `Command` nesnesi, veri döndürmek, verileri değiştirmek, saklı yordamları çalıştırmak ve parametre bilgilerini göndermek veya almak için veritabanı komutlarına erişim sağlar. `DataReader` veri kaynağından yüksek performanslı veri akışı sağlar. Son olarak, `DataAdapter` `DataSet` nesnesi ve veri kaynağı arasında köprü sağlar. `DataAdapter`, veri kaynağındaki SQL komutlarını yürütmek için `Command` nesneleri kullanarak `DataSet` verilerle birlikte yükler ve `DataSet` verilerde yapılan değişiklikleri veri kaynağına geri laştırır. Daha fazla bilgi için bkz. [veri sağlayıcıları .NET Framework](data-providers.md) ve [verileri alma ve değiştirme ADO.net](retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Veri kümesi  
 ADO.NET `DataSet`, herhangi bir veri kaynağından bağımsız olarak veri erişimi için özel olarak tasarlanmıştır. Sonuç olarak, birden çok ve farklı veri kaynaklarıyla birlikte kullanılabilir, XML verileriyle birlikte kullanılabilir veya uygulamada yerel verileri yönetmek için kullanılır. `DataSet`, veri satırlarından ve sütunlarından ve ayrıca birincil anahtar, yabancı anahtar, kısıtlama ve `DataTable` nesnelerdeki verilerle ilgili ilişki bilgileri içeren bir veya daha fazla <xref:System.Data.DataTable> nesnesinin bir koleksiyonunu içerir. Daha fazla bilgi için bkz. [veri kümeleri, DataTable ve DataView](./dataset-datatable-dataview/index.md).  
  
 Aşağıdaki diyagramda bir .NET Framework veri sağlayıcısı ve bir `DataSet`arasındaki ilişki gösterilmektedir.  
  
 ![ADO.Net grafiği](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
ADO.NET mimarisi  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>DataReader veya veri kümesi seçme  
 Uygulamanızın bir `DataReader` ( [DataReader kullanarak veri alma](retrieving-data-using-a-datareader.md)) veya bir `DataSet` (bkz. veri [kümeleri, DataTable ve DataView](./dataset-datatable-dataview/index.md)'ler) kullanması gerektiğine karar verirken, uygulamanızın gerektirdiği işlev türünü göz önünde bulundurun. Şunları yapmak için bir `DataSet` kullanın:  
  
- Verileri işleyebilmeniz için uygulamanızdaki yerel olarak önbelleğe alma. Yalnızca bir sorgunun sonuçlarını okumanız gerekiyorsa `DataReader` daha iyi bir seçenektir.  
  
- Katmanlar arasında veya bir XML Web hizmetinden uzak veriler.  
  
- Windows Forms denetimine bağlama veya birden fazla kaynaktaki verileri birleştirme ve ilişkilendirme gibi verilerle dinamik olarak etkileşime geçin.  
  
- Veri kaynağına açık bir bağlantı gerektirmeden veri üzerinde kapsamlı işlem gerçekleştirerek, bağlantıyı diğer istemciler tarafından kullanılmak üzere serbest bırakır.  
  
 `DataSet`tarafından sunulan işlevselliğe ihtiyacınız yoksa, verilerinizi yalnızca ileri, Salt okunabilir bir şekilde döndürmek için `DataReader` kullanarak uygulamanızın performansını artırabilirsiniz. `DataAdapter`, bir `DataSet` içeriğini doldurmak için `DataReader` kullansa da (bkz. [DataAdapter 'tan bir veri kümesini doldurma](populating-a-dataset-from-a-dataadapter.md)) `DataReader`, `DataSet`tarafından tüketilen belleği kaydedecağından ve `DataSet`içeriğini oluşturmak ve doldurmak için gereken işlemden kaçınmak için performansı artırabilir.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 LINQ to DataSet, veri kümesi nesnesinde önbelleğe alınan veriler üzerinde sorgu özellikleri ve derleme zamanı tür denetimi sağlar. Sorgular, C# veya Visual Basic gibi .NET Framework geliştirme dilinden birine yazmanızı sağlar. Daha fazla bilgi için [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 LINQ to SQL, bir ara kavramsal model kullanılmadan ilişkisel bir veritabanının veri yapılarına eşlenmiş bir nesne modeline karşı sorguları destekler. Her tablo ayrı bir sınıf tarafından temsil edilir ve nesne modelini ilişkisel veritabanı şemasına sıkı bir şekilde ayırır. LINQ to SQL, nesne modelindeki dil ile tümleşik sorguları Transact-SQL ' e çevirir ve yürütmek üzere veritabanına gönderir. Veritabanı sonuçları döndürdüğünde LINQ to SQL sonuçları nesnelere geri çevirir. Daha fazla bilgi için bkz. [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 ADO.NET Entity Framework, geliştiricilerin doğrudan ilişkisel bir depolama şemasına karşı programlama yerine kavramsal bir uygulama modeline karşı programlama yaparak veri erişimi uygulamaları oluşturmalarına olanak tanımak üzere tasarlanmıştır. Amaç, veri odaklı uygulamalar için gereken kod ve bakım miktarını azaltmaktır. Daha fazla bilgi için bkz. [ADO.NET Entity Framework](./ef/index.md).  
  
## <a name="wcf-data-services"></a>WCF Veri Hizmetleri  
 WCF Veri Hizmetleri, Web 'de veya intranette veri hizmetlerini dağıtmak için kullanılır. Veriler, Varlık Veri Modeli belirtimlerine göre varlıklar ve ilişkiler olarak yapılandırılır. Bu modelde dağıtılan verilere standart HTTP protokolü tarafından adreslenebilir. Daha fazla bilgi için [WCF Veri Hizmetleri 4.5](../wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML ve ADO.NET  
 ADO.NET, verilere bağlantısız erişim sağlamak için XML 'nin gücünden yararlanır. ADO.NET, .NET Framework içindeki XML sınıflarıyla birlikte tasarlanmıştır; her ikisi de tek bir mimarinin bileşenleridir.  
  
 ADO.NET ve .NET Framework XML sınıfları `DataSet` nesnesine yakınlardır. `DataSet` bir XML kaynağından alınan verilerle doldurulabilir ve bu dosya veya XML akışı olabilir. `DataSet`, `DataSet`verilerin kaynağından bağımsız olarak şemasını XML şeması tanım dili (XSD) şeması olarak içeren World Wide Web Consortium (W3C) uyumlu XML olarak yazılabilir. `DataSet` yerel seri hale getirme biçimi XML olduğundan, verileri katmanlar arasında taşımak için mükemmel bir ortamdır ve bir XML Web hizmetinden veya bir XML Web hizmetine veri ve şema bağlamı için en uygun seçim yaparak `DataSet`. Daha fazla bilgi için bkz. [XML belgeleri ve verileri](../../../standard/data/xml/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
