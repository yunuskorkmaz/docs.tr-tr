---
title: ADO.NET genel bakış
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 50881c05c8b6f2602d19817373a16e4661d3d133
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757950"
---
# <a name="adonet-overview"></a>ADO.NET genel bakış
ADO.NET veri kaynakları SQL Server ve XML gibi ve OLE DB ve ODBC ile kullanıma sunulan veri kaynaklarına tutarlı erişimi sağlar. Veri paylaşımı tüketici uygulamaları ADO.NET bu veri kaynaklarına bağlanmak ve alabilir, işlemek ve içerdikleri verileri güncelleştirmek için kullanabilirsiniz.  
  
 ADO.NET veri erişimini veri işleme ayrı ayrı veya dağıtımınızla birlikte kullanılabilir ayrık bileşenlere ayırır. ADO.NET bir veritabanına bağlanma, komutları çalıştırma ve sonuçları için .NET Framework veri sağlayıcısı içerir. Bu sonuçlar ya da doğrudan bir ADO.NET yerleştirilen işlenir <xref:System.Data.DataSet> kullanıcıya geçici bir şekilde kullanıma için nesne birden çok kaynak verilerle birlikte veya Katmanlar arasında geçirildi. `DataSet` Nesne da bağımsız bir .NET Framework veri sağlayıcısı için uygulama yerel verileri yönetmek için kullanılan veya XML'den kaynaklıdır.  
  
 ADO.NET sınıflarını System.Data.dll içinde bulunur ve System.Xml.dll içinde bulunan XML sınıflar ile tümleştirilir. Bir veritabanına bağlanan örnek kod verileri alır ve ardından bu verileri bir konsol penceresinde görüntüler için bkz: [ADO.NET kod örnekleri](../../../../docs/framework/data/adonet/ado-net-code-examples.md).  
  
 ADO.NET, yönetilen kod yerel Bileşen Nesne Modeli (COM) geliştiricilerine ActiveX Data Objects (ADO) tarafından sağlanan işlevleri benzer yazan geliştiriciler için işlevsellik sağlar. ADO.NET, değil ADO .NET uygulamalarınızın veri erişimi için kullanmanızı öneririz.  
  
 ADO.NET veri erişimi .NET Framework içinde en dolaysız yöntem sağlar. Temel alınan depolama modeli yerine kavramsal bir model karşı iş uygulamalarına izin veren bir üst düzey Özet için bkz: [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
 **Gizlilik bildirimi**: System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll ve System.Data.DataSetExtensions.dll derlemeler yapın bir kullanıcının özel veri özel olmayan veriler arasında ayrım.  Bu derlemeler değil toplamak, depolamak ve herhangi bir kullanıcının özel veri taşıma. Ancak, üçüncü taraf uygulamalar toplamak, depolamak veya bu derlemeler kullanarak bir kullanıcının özel veri taşıma.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ADO.NET Mimarisi](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 Mimarisine genel bakış ve ADO.NET bileşenlerinin sağlar.  
  
 [ADO.NET Teknoloji Seçenekleri ve Yönergeleri](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 Varlık veri platformuyla dahil teknolojileri ve ürünleri açıklar.  
  
 [LINQ ve ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 Dil ile tümleşik sorgu (LINQ) ADO.NET nasıl uygulandığı açıklanır ve ilgili konulara bağlantılar sağlar.  
  
 [.NET Framework Veri Sağlayıcıları](../../../../docs/framework/data/adonet/data-providers.md)  
 .NET Framework veri sağlayıcısı ve ADO.NET ile birlikte .NET Framework veri sağlayıcıları tasarım genel bir bakış sağlar.  
  
 [ADO.NET Veri Kümeleri](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 Genel bir bakış sağlar `DataSet` tasarım ve bileşenleri.  
  
 [ADO.NET’te Yan Yana Yürütme](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 ADO.NET sürümleri ve yan yana yürütme ve uygulama uyumluluğu üzerindeki etkilerini farklılıklar açıklanır.  
  
 [ADO.NET Kod Örnekleri](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 ADO.NET veri sağlayıcıları kullanarak verileri kod örnekleri sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET’teki Yenilikler](../../../../docs/framework/data/adonet/whats-new.md)  
 Yeni özellikler sunmaktadır [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Güvenli kodlama uygulamalarını ADO.NET kullanırken açıklar.  
  
 [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 .NET Framework veri türleri ve .NET Framework veri sağlayıcıları arasındaki veri türü eşlemeleri açıklar.  
  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Bir veri kaynağına bağlanmak, verileri almak ve veri değiştirme açıklar. Bu içerir `DataReaders` ve `DataAdapters`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [Visual Studio'da verilere erişime](/visualstudio/data-tools/accessing-data-in-visual-studio)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
