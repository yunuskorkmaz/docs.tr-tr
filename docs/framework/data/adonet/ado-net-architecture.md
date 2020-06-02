---
title: Mimari
description: 'Verilere erişmek ve veri işlemek için iki ana bileşeni de içeren ADO.NET mimarisi hakkında bilgi edinin: .NET Framework veri sağlayıcıları ve veri kümesi.'
ms.date: 03/30/2017
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
ms.openlocfilehash: 91e5b1e33ed1bc6e2acf6068a03bb8185324470d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287187"
---
# <a name="adonet-architecture"></a>ADO.NET Mimarisi
Veri işleme, temelde genellikle bağlantı tabanlı, iki katmanlı bir modele bağlıdır. Veri işleme giderek çok katmanlı mimarilerin kullanıldığı için programcılar, uygulamaları için daha iyi ölçeklenebilirlik sağlamak üzere bağlantısı kesilen bir yaklaşıma geçiş yapıyor.  
  
## <a name="adonet-components"></a>ADO.NET bileşenleri  
 Verilere erişmek ve veri işlemek için ADO.NET 'in iki ana bileşeni .NET Framework veri sağlayıcılarıdır ve ' dir <xref:System.Data.DataSet> .  
  
### <a name="net-framework-data-providers"></a>.NET Framework Veri Sağlayıcıları  
 .NET Framework veri sağlayıcıları doğrudan veri işleme ve hızlı, salt iletme, verilere salt okuma erişimi için tasarlanmış bileşenlerdir. `Connection`Nesnesi bir veri kaynağına bağlantı sağlar. `Command`Nesnesi, veri döndürmek, verileri değiştirmek, saklı yordamları çalıştırmak ve parametre bilgilerini göndermek veya almak için veritabanı komutlarına erişim sağlar. , `DataReader` Veri kaynağından yüksek performanslı veri akışı sağlar. Son olarak, `DataAdapter` `DataSet` nesnesi ve veri kaynağı arasında köprü sağlar. , `DataAdapter` Veri `Command` kaynağındaki SQL komutlarını yürütmek için nesneleri kullanır ve verileri veri `DataSet` kaynağına geri yüklemek ve içindeki verilerde yapılan değişiklikleri mutabık kılmak için kullanır `DataSet` . Daha fazla bilgi için bkz. [veri sağlayıcıları .NET Framework](data-providers.md) ve [verileri alma ve değiştirme ADO.net](retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Veri kümesi  
 ADO.NET, `DataSet` herhangi bir veri kaynağından bağımsız olarak veri erişimi için özel olarak tasarlanmıştır. Sonuç olarak, birden çok ve farklı veri kaynaklarıyla birlikte kullanılabilir, XML verileriyle birlikte kullanılabilir veya uygulamada yerel verileri yönetmek için kullanılır. , `DataSet` <xref:System.Data.DataTable> Veri satırlarından ve sütunlarından oluşan bir veya daha fazla nesnenin koleksiyonunu ve ayrıca birincil anahtar, yabancı anahtar, kısıtlama ve nesnelerdeki verilerle ilgili ilişki bilgilerini içerir `DataTable` . Daha fazla bilgi için bkz. [veri kümeleri, DataTable ve DataView](./dataset-datatable-dataview/index.md).  
  
 Aşağıdaki diyagramda bir .NET Framework veri sağlayıcısı ve ile arasındaki ilişki gösterilmektedir `DataSet` .  
  
 ![ADO.Net grafiği](./media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
ADO.NET mimarisi  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>DataReader veya veri kümesi seçme  
 Uygulamanızın bir `DataReader` ( [DataReader kullanarak veri alma](retrieving-data-using-a-datareader.md)) veya bir `DataSet` (bkz. veri [kümeleri, DataTable ve DataView](./dataset-datatable-dataview/index.md)) kullanması gerektiğine karar verirken, uygulamanızın gerektirdiği işlev türünü göz önünde bulundurun. `DataSet`Şunları yapmak için bir kullanın:  
  
- Verileri işleyebilmeniz için uygulamanızdaki yerel olarak önbelleğe alma. Yalnızca bir sorgunun sonuçlarını okumanız gerekiyorsa, `DataReader` daha iyi bir seçenektir.  
  
- Katmanlar arasında veya bir XML Web hizmetinden uzak veriler.  
  
- Windows Forms denetimine bağlama veya birden fazla kaynaktaki verileri birleştirme ve ilişkilendirme gibi verilerle dinamik olarak etkileşime geçin.  
  
- Veri kaynağına açık bir bağlantı gerektirmeden veri üzerinde kapsamlı işlem gerçekleştirerek, bağlantıyı diğer istemciler tarafından kullanılmak üzere serbest bırakır.  
  
 Tarafından sağlanmış işlevselliğe ihtiyacınız yoksa, `DataSet` `DataReader` verilerinizi yalnızca ileri, Salt okunabilir bir şekilde döndürmek için kullanarak uygulamanızın performansını artırabilirsiniz. , `DataAdapter` `DataReader` Öğesinin içeriğini doldurmak için `DataSet` (bkz. [DataAdapter 'Dan bir veri kümesini doldurma](populating-a-dataset-from-a-dataadapter.md)) kullanmasına karşın, kullanarak, `DataReader` tarafından tüketilen belleği kaydedecağından `DataSet` ve içeriğini oluşturmak ve doldurmak için gereken işlemden kaçınmak için performansı artırabilir `DataSet` .  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 LINQ to DataSet, veri kümesi nesnesinde önbelleğe alınan veriler üzerinde sorgu özellikleri ve derleme zamanı tür denetimi sağlar. C# veya Visual Basic gibi .NET Framework geliştirme dilinden birine sorgu yazmanızı sağlar. Daha fazla bilgi için bkz. [LINQ to DataSet](linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 LINQ to SQL, bir ara kavramsal model kullanılmadan ilişkisel bir veritabanının veri yapılarına eşlenmiş bir nesne modeline karşı sorguları destekler. Her tablo ayrı bir sınıf tarafından temsil edilir ve nesne modelini ilişkisel veritabanı şemasına sıkı bir şekilde ayırır. LINQ to SQL, nesne modelindeki dil ile tümleşik sorguları Transact-SQL ' e çevirir ve yürütmek üzere veritabanına gönderir. Veritabanı sonuçları döndürdüğünde LINQ to SQL sonuçları nesnelere geri çevirir. Daha fazla bilgi için bkz. [LINQ to SQL](./sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 ADO.NET Entity Framework, geliştiricilerin doğrudan ilişkisel bir depolama şemasına karşı programlama yerine kavramsal bir uygulama modeline karşı programlama yaparak veri erişimi uygulamaları oluşturmalarına olanak tanımak üzere tasarlanmıştır. Amaç, veri odaklı uygulamalar için gereken kod ve bakım miktarını azaltmaktır. Daha fazla bilgi için bkz. [ADO.NET Entity Framework](./ef/index.md).  
  
## <a name="wcf-data-services"></a>WCF Veri Hizmetleri  
 WCF Veri Hizmetleri, Web 'de veya intranette veri hizmetlerini dağıtmak için kullanılır. Veriler, Varlık Veri Modeli belirtimlerine göre varlıklar ve ilişkiler olarak yapılandırılır. Bu modelde dağıtılan verilere standart HTTP protokolü tarafından adreslenebilir. Daha fazla bilgi için bkz. [WCF Veri Hizmetleri 4,5](../wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML ve ADO.NET  
 ADO.NET, verilere bağlantısız erişim sağlamak için XML 'nin gücünden yararlanır. ADO.NET, .NET Framework içindeki XML sınıflarıyla birlikte tasarlanmıştır; her ikisi de tek bir mimarinin bileşenleridir.  
  
 ADO.NET ve .NET Framework XML sınıfları nesnesine yakınlardır `DataSet` . , `DataSet` BIR XML kaynağından alınan verilerle doldurulabilir ve bunun bir dosya veya XML akışı olması olabilir. , `DataSet` İçindeki verilerin kaynağına bakılmaksızın ŞEMASıNı XML şeması tanım dili (xsd) şeması olarak Içeren World Wide Web Consortium (W3C) uyumlu XML olarak yazılabilir `DataSet` . XML 'nin yerel seri hale getirme biçimi nedeniyle `DataSet` , verileri katmanlar arasında taşımak için mükemmel bir ortamdır; bu, `DataSet` verileri ve şema bağlamını bir XML Web hizmetinden ve bir XML Web hizmetinden uzak hale getirmek için en uygun seçeneği sağlar. Daha fazla bilgi için bkz. [XML belgeleri ve verileri](../../../standard/data/xml/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
