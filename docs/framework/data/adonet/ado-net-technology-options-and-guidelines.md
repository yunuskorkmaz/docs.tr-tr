---
title: ADO.NET Teknoloji Seçenekleri ve Yönergeleri
ms.date: 03/30/2017
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
ms.openlocfilehash: d0f363d5eb102edf965c9c6068873fce0721d288
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785777"
---
# <a name="adonet-technology-options-and-guidelines"></a>ADO.NET Teknoloji Seçenekleri ve Yönergeleri
ADO.NET veri platformu, geliştiriciler için gereken kodlama ve bakım miktarını, kavramsal varlık veri modellerine karşı programlamalarına izin verecek şekilde azaltmak için çok bölgeli bir stratejidir. Bu platform, ADO.NET Entity Framework ve ilgili teknolojileri içerir.  
  
## <a name="entity-framework"></a>Varlık Çerçevesi  
 ADO.NET Entity Framework, geliştiricilerin doğrudan ilişkisel bir depolama şemasına karşı programlama yerine kavramsal bir uygulama modeline karşı programlama yaparak veri erişimi uygulamaları oluşturmalarına olanak tanımak üzere tasarlanmıştır. Amaç, veri odaklı uygulamalar için gereken kod ve bakım miktarını azaltmaktır. Daha fazla bilgi için bkz. [ADO.NET Entity Framework](./ef/index.md).  
  
### <a name="entity-data-model-edm"></a>Varlık Veri Modeli (EDM)  
 Varlık Veri Modeli (EDM), uygulama verilerini varlık ve ilişki kümeleri olarak tanımlayan bir tasarım belirtimidir. Bu modeldeki veriler, nesne ilişkisel eşlemeyi ve uygulama sınırları genelinde veri programlamasına olanak destekler.  
  
### <a name="object-services"></a>Nesne Hizmetleri  
 Nesne Hizmetleri, programcıların ortak dil çalışma zamanı (CLR) sınıfları kümesi aracılığıyla kavramsal modelle etkileşime geçmesini sağlar. Bu sınıflar kavramsal modelden otomatik olarak oluşturulabilir veya kavramsal modelin yapısını yansıtmak için bağımsız olarak geliştirilebilir. Ayrıca, nesne Hizmetleri, durum yönetimi, değişiklik izleme, kimlik çözümlemesi, ilişkileri yükleme ve gezinme, nesne değişikliklerini veritabanı değişikliklerine yayma gibi hizmetler de dahil olmak üzere Entity Framework için altyapı desteği sağlar, ve Entity SQL için sorgu oluşturma desteği. Daha fazla bilgi için bkz. [nesne hizmetlerine genel bakış (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).  
  
### <a name="linq-to-entities"></a>LINQ - Varlıklar  
 LINQ to Entities, geliştiricilerin LINQ ifadelerini ve LINQ standart sorgu işleçlerini kullanarak Entity Framework nesne bağlamına karşı kesin olarak yazılmış sorgular oluşturmalarına olanak tanıyan dil ile tümleşik bir sorgu (LINQ) uygulamasıdır. LINQ to Entities, geliştiricilerin Microsoft SQL Server ve üçüncü taraf veritabanları arasında çok esnek bir nesne ilişkisel eşleme ile kavramsal bir modele karşı çalışmasını sağlar. Daha fazla bilgi için bkz. [LINQ to Entities](./ef/language-reference/linq-to-entities.md).  
  
### <a name="entity-sql"></a>Varlık SQL  
 Entity SQL, bir Varlık Veri Modeli etkileşimde bulunmak için tasarlanan metin tabanlı bir sorgu dilidir. Entity SQL, devralma, karmaşık türler ve açık ilişkiler gibi daha üst düzey modelleme kavramları açısından sorgu oluşturma yapıları içeren bir SQL diyalekti. Geliştiriciler ayrıca doğrudan nesne hizmetleriyle Entity SQL de kullanabilir. Daha fazla bilgi için bkz. [Entity SQL Language](./ef/language-reference/entity-sql-language.md).  
  
### <a name="entityclient"></a>EntityClient  
 EntityClient, bir Varlık Veri Modeli etkileşim kurmak için kullanılan yeni bir .NET Framework veri sağlayıcısıdır. EntityClient, ortaya <xref:System.Data.EntityClient.EntityConnection> çıkaran .NET Framework veri sağlayıcısı modelini ve <xref:System.Data.EntityClient.EntityCommand> döndüren <xref:System.Data.EntityClient.EntityDataReader>nesneleri izler. EntityClient, Entity SQL diliyle çalışarak, depolamaya özgü veri sağlayıcılarına esnek eşleme sağlar. Daha fazla bilgi için bkz. [Entity Framework Için EntityClient sağlayıcısı](./ef/entityclient-provider-for-the-entity-framework.md).  
  
### <a name="entity-data-model-tools"></a>Varlık veri modeli araçları  
 Entity Framework, EDM uygulamaları oluşturmayı kolaylaştırmak için komut satırı araçları, sihirbazlar ve tasarımcılar sağlar. EntityDataSource denetimi, EDM tabanlı veri bağlama senaryolarını destekler. EntityDataSource denetiminin programlama yüzeyi, Visual Studio 'daki diğer veri kaynağı denetimlerine benzer. Daha fazla bilgi için bkz. [ADO.NET varlık veri modeli araçları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100)).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 LINQ to SQL, .NET Framework sınıfları kullanarak SQL Server veritabanını modelleyerek bir nesne ilişkisel eşleme (veya/e) uygulamasıdır. LINQ to SQL, LINQ kullanarak veritabanınızı sorgulamanızı ve verileri güncelleştirme, ekleme ve silme gibi verileri de silebilir. LINQ to SQL, veri doğrulama ve iş mantığı kurallarını veri modelinize tümleştirmenin kolay bir yolunu sağlayan işlemler, görünümler ve saklı yordamları destekler. Bir veritabanındaki nesneleri temel alan varlık sınıflarını ve ilişkilendirmelerini modellemek için Nesne İlişkisel Tasarımcısı (O/R Designer) kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'da LINQ to SQL araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
## <a name="wcf-data-services"></a>WCF Veri Hizmetleri  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Web üzerinde veya bir intranette veri Hizmetleri dağıtır. Veriler, Varlık Veri Modeli belirtimlerine göre varlıklar ve ilişkiler olarak yapılandırılır. Bu modelde dağıtılan verilere standart HTTP protokolü tarafından adreslenebilir. Daha fazla bilgi için [WCF Veri Hizmetleri 4.5](../wcf/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’e Genel Bakış](ado-net-overview.md)
- [ADO.NET’teki Yenilikler](whats-new.md)
