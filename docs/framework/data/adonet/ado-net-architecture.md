---
title: ADO.NET mimarisi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcd45b99-ae8f-45ab-8b97-d887beda734e
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 227bef975a54676ceda5f922ed02f98c27fc8759
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="adonet-architecture"></a>ADO.NET mimarisi
Veri işleme, geleneksel öncelikle tabanlı bağlantısı, iki katmanlı model üzerinde dayanıyordu. Veri işleme çok katmanlı mimarileri giderek kullanır gibi kendi uygulamaları için daha iyi ölçeklenebilirlik sağlamak için bağlantısı kesik bir yaklaşım için programcıları geçiliyor.  
  
## <a name="adonet-components"></a>ADO.NET bileşenleri  
 İki ana bileşenlerinin [!INCLUDE[ado_orcas_long](../../../../includes/ado-orcas-long-md.md)] erişme ve verileri yönlendirmek için [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcıları ve <xref:System.Data.DataSet>.  
  
### <a name="net-framework-data-providers"></a>.NET framework veri sağlayıcıları  
 .NET Framework veri sağlayıcıları açıkça veri işleme ve veri hızlı, yalnızca iletme, salt okunur erişim için tasarlanmış bileşenleridir. `Connection` Nesnesi, bir veri kaynağı bağlantısı sağlar. `Command` Nesne dönüş verileri, verileri değiştirme, saklı yordamları çalıştırmak ve gönderme veya parametre bilgilerini almak için veritabanı komutları erişim sağlar. `DataReader` Yüksek performanslı akış veri kaynağından veri sağlar. Son olarak, `DataAdapter` arasında köprü sağlar `DataSet` nesne ve veri kaynağı. `DataAdapter` Kullanan `Command` hem yük veri kaynağında SQL komutlarını çalıştırmak için nesneleri `DataSet` verilerle ve verilerde yapılan değişiklikler mutabık kılmak `DataSet` veri kaynağına geri. Daha fazla bilgi için bkz: [.NET Framework veri sağlayıcıları](../../../../docs/framework/data/adonet/data-providers.md) ve [alınıyor ve ADO.NET veri değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md).  
  
### <a name="the-dataset"></a>Veri kümesi  
 ADO.NET `DataSet` açıkça herhangi bir veri kaynağı bağımsız veri erişimi için tasarlanmıştır. Sonuç olarak, birden fazla ile kullanılabilir ve farklı veri kaynakları, XML verileriyle kullanılan veya uygulamaya yerel verileri yönetmek için kullanılan. `DataSet` Bir veya daha fazla koleksiyonu içeren <xref:System.Data.DataTable> satırları ve sütunları veri ve birincil anahtar, yabancı anahtar, kısıtlama ve ilişkisi hakkındaki bilgilerin verileri oluşan nesneleri `DataTable` nesneleri. Daha fazla bilgi için bkz: [veri kümeleri, DataTable ve DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Aşağıdaki diyagram arasındaki ilişkiyi gösterir bir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri sağlayıcısı ve `DataSet`.  
  
 ![ADO.Net grafiği](../../../../docs/framework/data/adonet/media/ado-1-bpuedev11.png "ado_1_bpuedev11")  
ADO.NET mimarisi  
  
### <a name="choosing-a-datareader-or-a-dataset"></a>DataReader veya bir veri kümesi seçme  
 Karar verdiğinizde, uygulamanızın kullanması gerekip gerekmediğini bir `DataReader` (bkz [alma verileri kullanarak bir DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)) veya bir `DataSet` (bkz [veri kümeleri, DataTable ve DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)), türünü göz önünde bulundurun uygulamanızın gerektirdiği işlevselliği. Kullanım bir `DataSet` aşağıdakileri yapmak için:  
  
-   Böylece üzerinde çalışabilirsiniz veri uygulamanızı yerel olarak önbelleğe alır. Yalnızca bir sorgunun sonuçlarını okumak gerekiyorsa `DataReader` daha iyi bir seçimdir.  
  
-   Uzak veri katmanları arasında veya XML Web Hizmetleri.  
  
-   Bir Windows Forms denetimi bağlama veya birleştirme ve birden fazla kaynaktan veri ilgili gibi dinamik veri ile etkileşim.  
  
-   Kapsamlı işleme, diğer istemciler tarafından kullanılacak bağlantı boşaltır veri kaynağına açık bir bağlantı gerektirmeden verileri gerçekleştirin.  
  
 Tarafından sağlanan işlevleri gerektirmiyorsa `DataSet`, kullanarak, uygulamanızın performansını artırabilir `DataReader` verilerinizi salt iletme ve salt okunur bir şekilde geri dönmek için. Ancak `DataAdapter` kullanan `DataReader` içeriğini doldurmak için bir `DataSet` (bkz [DataAdapter kümesinden doldurma](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)), kullanarak `DataReader`, bellek kaydedecek olduğundan performansı artırabilir tüketilen tarafından `DataSet`ve oluşturup içeriğini doldurmak için gereken işleme engel `DataSet`.  
  
## <a name="linq-to-dataset"></a>LINQ - DataSet  
 LINQ-DataSet sorgu özellikleri ve derleme zamanı tür bir veri kümesi nesnesi önbelleğe alınan veriler üzerinde denetlemesini sağlar. Bir .NET Framework geliştirme dil C# veya Visual Basic gibi sorguları yazma sağlar. Daha fazla bilgi için bkz: [LINQ-DataSet](../../../../docs/framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 LINQ-SQL Ara kavramsal bir model kullanmadan bir ilişkisel veritabanı veri yapılarını eşlenen bir nesne modeli sorguları destekler. Her tablo nesne modeli ilişkisel veritabanı şemasında sıkı bir şekilde Kuplaj ayrı bir sınıfı temsil edilir. LINQ-SQL dil ile tümleşik sorgu nesne modelinde Transact-SQL dönüşür ve bunları yürütme için veritabanı gönderir. LINQ-SQL veritabanı sonuçları döndürdüğünde, sonuçları nesnelerini geri çevirir. Daha fazla bilgi için bkz: [LINQ-SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 ADO.NET Entity Framework, doğrudan bir ilişkisel depolama şema karşı programlama yerine kavramsal uygulama modeli karşı programlama geliştiricilerin veri erişimi uygulamaları oluşturmalarına olanak sağlamak için tasarlanmıştır. Kod ve veri odaklı uygulamalar için gereken bakım miktarını azaltmak için belirtilir. Daha fazla bilgi için bkz: [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
## <a name="wcf-data-services"></a>WCF Veri Hizmetleri  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Veri Hizmetleri Web ya da intranet üzerinde dağıtmak için kullanılır. Veri varlıkları ve ilişkileri varlık veri modeli belirtimlerine uygun olarak yapılandırılmıştır. Bu modelde dağıtılan standart HTTP protokolü tarafından adreslenebilir verilerdir. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="xml-and-adonet"></a>XML ve ADO.NET  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]veri bağlantısı kesilmiş erişim sağlamak için XML gücünü yararlanır. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]tasarlanmış el el ile XML sınıflarda edildi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; her ikisi de tek bir mimari bileşenleridir.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]ve XML sınıflarda [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] içinde yakınsama `DataSet` nesnesi. `DataSet` Bir dosya veya bir XML akışı olup, bir XML kaynağı verilerle doldurulabilir. `DataSet` XML Şeması Tanım Dili (XSD) şeması, veri kaynağını bakılmaksızın olarak şemasına içeren World Wide Web Konsorsiyumu (W3C) uyumlu XML olarak yazılmış `DataSet`. Yerel seri hale getirme biçimi nedeniyle `DataSet` XML, yapmadan katmanlar arasında verileri taşımak için mükemmel bir medium'dur `DataSet` remoting veri ve şema bağlamı için bir en iyi seçim XML Web hizmetleri gelen ve giden. Daha fazla bilgi için bkz: [XML belgeler ve veriler](../../../../docs/standard/data/xml/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET genel bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
