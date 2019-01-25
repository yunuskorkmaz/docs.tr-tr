---
title: ADO.NET teknoloji seçenekleri ve yönergeleri
ms.date: 03/30/2017
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
ms.openlocfilehash: 2550c286485025a394cf3f8afe6c43a0472b2cd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566287"
---
# <a name="adonet-technology-options-and-guidelines"></a>ADO.NET teknoloji seçenekleri ve yönergeleri
ADO.NET veri platformu, kodlama ve kavramsal varlık veri modelleri karşı programlamak için sağlayarak geliştiriciler için gerekli bakım miktarını azaltmak için bir çoklu sürüm stratejisidir. Bu platform, ADO.NET varlık çerçevesi ve ilgili teknolojileri içerir.  
  
## <a name="entity-framework"></a>Varlık Çerçevesi  
 ADO.NET Entity Framework, doğrudan bir ilişkisel depolama şemaya karşı programlama yerine bir uygulama kavramsal modeline karşı programlama geliştiricilerin veri erişimi uygulamaları etkinleştirmek için tasarlanmıştır. Kod ve veri odaklı uygulamalar için gerekli bakım miktarını azaltmak için hedeftir. Daha fazla bilgi için [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
### <a name="entity-data-model-edm"></a>Varlık Veri Modeli (EDM)  
 Varlık veri modeli (EDM) varlıkları ve ilişkileri ayarlar gibi uygulama verilerini tanımlayan bir tasarım özelliğidir. Bu modelde veriler, nesne ilişkisel eşleme ve veri programlama uygulama sınırlarında destekler.  
  
### <a name="object-services"></a>Nesne Hizmetleri  
 Nesne Hizmetleri programcıların kavramsal model bir dizi ortak dil çalışma zamanı (CLR) sınıfları aracılığıyla etkileşim sağlar. Bu sınıfların kavramsal modelden otomatik olarak oluşturulabilir veya kavramsal model yapısını yansıtmak için bağımsız olarak geliştirilebilir. Nesne Hizmetleri, varlık durum yönetimi, değişiklik izleme, kimlik çözümlemesi gibi hizmetleri de dahil olmak üzere yükleme ve ilişkileri, nesne değişiklikleri için veritabanı değişikliklerini yayma gezinme çerçevesi, altyapı desteği de sağlar, ve sorgu varlık SQL desteği oluşturma. Daha fazla bilgi için [nesne hizmetlerine genel bakış (Entity Framework)](https://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
### <a name="linq-to-entities"></a>LINQ - Varlıklar  
 LINQ to Entities LINQ ifadeleri ve LINQ standart sorgu işleçleri kullanarak Entity Framework nesne bağlamı kesin türü belirtilmiş sorguları oluşturmak geliştiricilerinin sağlayan bir dil ile tümleşik sorgu (LINQ) uygulamasıdır. LINQ to Entities, geliştiricilerin Microsoft SQL Server ve üçüncü taraf veritabanları çok esnek bir nesne ilişkisel eşleme kavramsal bir modelle karşı çalışan olanak tanır. Daha fazla bilgi için [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
### <a name="entity-sql"></a>Varlık SQL  
 Entity SQL bir varlık veri modeli ile etkileşime geçmek için tasarlanmış bir metin tabanlı sorgu dilidir. SQL devralma, karmaşık türler ve açık ilişkileri gibi daha üst düzey modelleme kavramları açısından sorgulamak için yapıları içeren bir SQL diyalekti varlıktır. Geliştiriciler, varlık SQL doğrudan nesne hizmetlerle de kullanabilirsiniz. Daha fazla bilgi için [Entity SQL dili](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
### <a name="entityclient"></a>EntityClient  
 EntityClient, bir varlık veri modeli ile etkileşim kurmak için kullanılan yeni bir .NET Framework Veri Sağlayıcısı ' dir. EntityClient gösterme, .NET Framework Veri Sağlayıcı modelini izler <xref:System.Data.EntityClient.EntityConnection> ve <xref:System.Data.EntityClient.EntityCommand> nesneleri döndüren bir <xref:System.Data.EntityClient.EntityDataReader>. EntityClient, depolama özgü veri sağlayıcıları için esnek eşlemesi Entity SQL dili ile çalışır. Daha fazla bilgi için [EntityClient ve varlık SQL](https://msdn.microsoft.com/library/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
### <a name="entity-data-model-tools"></a>Varlık veri modeli araçları  
 Komut satırı araçları, sihirbazlar ve tasarımcılar EDM oluşturmayı kolaylaştırmak için Entity Framework sağlayan uygulamalar. EntityDataSource denetim üzerinde EDM temel veri bağlama senaryoları destekler. Programlama yüzey EntityDataSource denetimin diğer veri kaynağı denetimleri Visual Studio'da benzer. Daha fazla bilgi için [ADO.NET varlık veri modeli Araçları](https://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 LINQ to SQL olan bir nesne ilişkisel eşleme (veya / M) uygulamasında, .NET Framework sınıfları kullanarak bir SQL Server veritabanı modeli sağlar. LINQ to SQL LINQ kullanarak veritabanını sorgulama olanak tanır yanı sıra güncelleştirme, eklemek ve verileri silin. Verileri doğrulama ve iş mantığı kuralları, veri modelinizi tümleştirmeniz için kolay bir yol sağlama işlemleri, görünümler ve saklı yordamlar, LINQ to SQL destekler. Varlık sınıfları ve nesneleri bir veritabanında temel alan ilişkileri modellemek için Object Relational Designer (O/R Tasarımcısı) kullanabilirsiniz. Daha fazla bilgi için [LINQ to SQL araçlarını Visual Studio'da](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
## <a name="wcf-data-services"></a>WCF Veri Hizmetleri  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Veri Hizmetleri Web veya intranet dağıtır. Veri varlıkları ve ilişkileri varlık veri modeli belirtimlere göre olarak yapılandırılmıştır. Bu modelde dağıtılan standart HTTP protokolü tarafından adreslenebilir verilerdir. Daha fazla bilgi için [WCF Veri Hizmetleri 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET’teki Yenilikler](../../../../docs/framework/data/adonet/whats-new.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
