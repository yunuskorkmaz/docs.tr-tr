---
title: ADO.NET’e Genel Bakış
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 7ec3b5f4dd08a39f96ed28e6666fd4b00bced903
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170071"
---
# <a name="adonet-overview"></a>ADO.NET’e Genel Bakış
ADO.NET veri kaynağına OLE DB ve ODBC kullanıma sunulan ve SQL Server ve XML gibi veri kaynaklarına tutarlı erişimi sağlar. Veri paylaşımı tüketici uygulamaları, ADO.NET, bu veri kaynağına bağlanın ve almak, işlemek ve içerdikleri verileri güncelleştirmek için kullanabilirsiniz.  
  
 ADO.NET veri erişimi veri işleme ayrı olarak veya art arda kullanılan ayrık bileşenlere ayırır. ADO.NET, bir veritabanına bağlanma, komutları çalıştırarak ve sonuçları almak için .NET Framework veri sağlayıcıları içerir. Sonuçları ya da doğrudan bir ADO.NET yerleştirilen işlenir <xref:System.Data.DataSet> kullanıcıya geçici bir biçimde açığa için nesne birden çok kaynaktan alınan verilerle birlikte veya Katmanlar arasında geçirilen. `DataSet` Nesne de uygulamanın yerel verileri yönetmek için bir .NET Framework veri sağlayıcısı bağımsız olarak kullanılabilir veya XML'den kaynaklanan.  
  
 ADO.NET sınıflarını System.Data.dll içinde bulunur ve System.Xml.dll içinde bulunan XML sınıfları ile tümleştirilir. Örnek kod, bir veritabanına bağlanan verileri buradan alır ve ardından bu verileri bir konsol penceresinde görüntüler için bkz: [ADO.NET kod örnekleri](../../../../docs/framework/data/adonet/ado-net-code-examples.md).  
  
 ADO.NET, yönetilen kodun yerel Bileşen Nesne Modeli (COM) geliştiricileri için ActiveX Data Objects (ADO) tarafından sağlanan işlevselliği için benzer yazma geliştiriciler için işlevsellik sağlar. ADO.NET, değil ADO .NET uygulamalarınıza veri erişimi için kullanmanızı öneririz.  
  
 ADO.NET, .NET Framework içindeki veri erişiminin en dolaysız yöntem sağlar. Temel alınan depolama modelinin yerine kavramsal bir modeli karşı çalışmaya uygulamalarına izin veren bir daha yüksek düzeyde soyutlama için bkz. [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
 **Gizlilik bildirimi**: Bir kullanıcının arasında System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll'ye ve System.Data.DataSetExtensions.dll derlemeleri ayırt etmez özel veriler ve özel olmayan veri.  Bu derlemeler değil toplamak, depolamak veya herhangi bir kullanıcının özel veri taşıma. Ancak, üçüncü taraf uygulamalar toplamak, depolamak veya bu bütünleştirilmiş kodları kullanan bir kullanıcının özel veri taşıma.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [ADO.NET Mimarisi](../../../../docs/framework/data/adonet/ado-net-architecture.md)  
 Mimarisine genel bakış ve ADO.NET bileşenleri sağlar.  
  
 [ADO.NET Teknoloji Seçenekleri ve Yönergeleri](../../../../docs/framework/data/adonet/ado-net-technology-options-and-guidelines.md)  
 Varlık Veri Platformu ile dahil teknolojileri ve ürünleri açıklar.  
  
 [LINQ ve ADO.NET](../../../../docs/framework/data/adonet/linq-and-ado-net.md)  
 ADO.NET dil ile tümleşik sorgu (LINQ) nasıl uygulandığını açıklar ve ilgili konulara bağlantılar sağlar.  
  
 [.NET Framework Veri Sağlayıcıları](../../../../docs/framework/data/adonet/data-providers.md)  
 .NET Framework veri sağlayıcısı ve ADO.NET ile birlikte .NET Framework veri sağlayıcıları tasarıma genel bir bakış sağlar.  
  
 [ADO.NET Veri Kümeleri](../../../../docs/framework/data/adonet/ado-net-datasets.md)  
 Genel bir bakış sağlar `DataSet` tasarım ve bileşenleri.  
  
 [ADO.NET’te Yan Yana Yürütme](../../../../docs/framework/data/adonet/side-by-side-execution.md)  
 ADO.NET sürümleri ve yan yana yürütme ve uygulama uyumluluk etkileri farklılıkları açıklar.  
  
 [ADO.NET Kod Örnekleri](../../../../docs/framework/data/adonet/ado-net-code-examples.md)  
 ADO.NET veri sağlayıcıları kullanarak veri kod örneği sağlanmıştır.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [ADO.NET’teki Yenilikler](../../../../docs/framework/data/adonet/whats-new.md)  
 Yeni özellikleri tanıtır [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].  
  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 Güvenli kodlama yöntemleri ADO.NET kullanırken açıklar.  
  
 [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 .NET Framework veri türleri ve .NET Framework veri sağlayıcıları arasında veri türü eşlemeleri açıklar.  
  
 [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 Bir veri kaynağına bağlanmak, verileri almak ve verileri değiştirme işlemini açıklamaktadır. Bu içerir `DataReaders` ve `DataAdapters`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [Visual Studio'da verilere erişme](/visualstudio/data-tools/accessing-data-in-visual-studio)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
