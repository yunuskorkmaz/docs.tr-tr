---
title: "ADO.NET teknoloji seçenekleri ve yönergeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aa4cefb27ff3fde3f4f31d996a80b19b94ea57e2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="adonet-technology-options-and-guidelines"></a>ADO.NET teknoloji seçenekleri ve yönergeleri
ADO.NET veri platformu, kodlama ve kavramsal varlık veri modellerde programlamak için bunları etkinleştirerek geliştiriciler için gerekli bakım miktarını azaltmak için bir çoklu yayın stratejidir. Bu platform ADO.NET Entity Framework ve ilgili teknolojileri içerir.  
  
## <a name="entity-framework"></a>Varlık Çerçevesi  
 ADO.NET Entity Framework, doğrudan bir ilişkisel depolama şema karşı programlama yerine kavramsal uygulama modeli karşı programlama geliştiricilerin veri erişimi uygulamaları oluşturmalarına olanak sağlamak için tasarlanmıştır. Kod ve veri odaklı uygulamalar için gereken bakım miktarını azaltmak için belirtilir. Daha fazla bilgi için bkz: [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md).  
  
### <a name="entity-data-model-edm"></a>Varlık Veri Modeli (EDM)  
 Varlık veri modeli (EDM) varlıkları ve ilişkileri ayarlar gibi uygulama verileri tanımlayan bir tasarım belirtimidir. Bu modelde veri nesne ilişkisel eşleme ve veri programlama uygulama sınırlarında destekler.  
  
### <a name="object-services"></a>Object Services  
 Nesne Hizmetleri programcıların kavramsal model bir dizi ortak dil çalışma zamanı (CLR) sınıfları aracılığıyla etkileşim sağlar. Bu sınıfların kavramsal modelden otomatik olarak oluşturulabilir veya bağımsız olarak kavramsal model yapısını yansıtacak şekilde geliştirilebilir. Nesne hizmetleri de varlık durum yönetimi, değişiklik izleme, kimlik çözünürlüğü gibi hizmetleri dahil olmak üzere yüklemek ve ilişkileri, nesne değişiklikleri veritabanı değişikliklerine yayılıyor gezinme Framework için altyapı destek sağlar, ve varlık SQL desteği sorgu oluşturma. Daha fazla bilgi için bkz: [nesne Hizmetleri'ne Genel Bakış (Entity Framework)](http://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).  
  
### <a name="linq-to-entities"></a>LINQ - Varlıklar  
 LINQ to Entities sorguları Entity Framework nesne bağlamı kesin türü belirtilmiş LINQ ifadeleri ve LINQ standart sorgu işleçleri kullanarak oluşturmak geliştiriciler izin veren bir dil ile tümleşik sorgu (LINQ) uygulamasıdır. LINQ to Entities geliştiricilerin kavramsal modelde çok esnek bir nesne ilişkisel eşleme ile Microsoft SQL Server ve üçüncü taraf veritabanları arasında iş olanak tanır. Daha fazla bilgi için bkz: [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
### <a name="entity-sql"></a>Varlık SQL  
 Varlık SQL bir varlık veri modeli ile etkileşim kurmak için tasarlanmış bir metin tabanlı sorgu dildir. SQL devralma, karmaşık türler ve açık ilişkileri gibi daha üst düzey modelleme kavramları bakımından sorgulamak için yapıları içeren bir SQL dialect varlıktır. Geliştiricilerin, doğrudan nesne hizmetleriyle varlık SQL de kullanabilirsiniz. Daha fazla bilgi için bkz: [varlık SQL dil](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md).  
  
### <a name="entityclient"></a>EntityClient  
 EntityClient bir varlık veri modeli ile etkileşmek için kullanılan yeni bir .NET Framework Veri Sağlayıcısı'dır. EntityClient gösterme .NET Framework veri sağlayıcısı düzenini izler <xref:System.Data.EntityClient.EntityConnection> ve <xref:System.Data.EntityClient.EntityCommand> nesneleri bu iade bir <xref:System.Data.EntityClient.EntityDataReader>. EntityClient, depolama özgü veri sağlayıcıları için esnek eşlemesi varlık SQL dili ile çalışır. Daha fazla bilgi için bkz: [EntityClient ve varlık SQL](http://msdn.microsoft.com/library/49202ab9-ac98-4b4b-a05c-140e422bf527).  
  
### <a name="entity-data-model-tools"></a>Varlık veri modeli araçları  
 Komut satırı araçları, sihirbazları ve tasarımcıları EDM oluşturmayı kolaylaştırmak için Entity Framework sağlayan uygulamalar. EntityDataSource denetimi üzerinde EDM temel veri bağlama senaryoları destekler. Diğer veri kaynağı denetimleri Visual Studio'da EntityDataSource denetim programlama yüzeyinin benzer. Daha fazla bilgi için bkz: [ADO.NET varlık veri modeli Araçları](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527).  
  
## <a name="linq-to-sql"></a>LINQ - SQL  
 LINQ-SQL olan bir nesne ilişkisel eşleme (veya / M) uygulamasında, .NET Framework sınıfları kullanarak bir SQL Server veritabanı modeli sağlar. LINQ-SQL LINQ, kullanarak veritabanınızı sorgu olanak tanır yanı sıra güncelleştirme, ekleme ve veri silmek. LINQ-SQL, veri doğrulama ve iş mantığı kuralları, veri modeline tümleştirmeniz için kolay bir yol sağlama işlemleri, görünümler ve saklı yordamlar destekler. Sınıflar ve bir veritabanındaki nesnelerde dayalı ilişkileri modellemek için Nesne İlişkisel Tasarımcısı (O/R Tasarımcısı) kullanabilirsiniz. Daha fazla bilgi için bkz: [LINQ-SQL Visual Studio Araçları](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).  
  
## <a name="wcf-data-services"></a>WCF Veri Hizmetleri  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]Veri Hizmetleri Web veya intranet üzerinde dağıtır. Veri varlıkları ve ilişkileri varlık veri modeli belirtimlerine uygun olarak yapılandırılmıştır. Bu modelde dağıtılan standart HTTP protokolü tarafından adreslenebilir verilerdir. Daha fazla bilgi için bkz: [WCF Veri Hizmetleri 4.5](../../../../docs/framework/data/wcf/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [ADO.NET’teki Yenilikler](../../../../docs/framework/data/adonet/whats-new.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
