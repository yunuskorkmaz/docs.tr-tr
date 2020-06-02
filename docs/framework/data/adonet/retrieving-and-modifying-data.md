---
title: Verileri alma ve değiştirme
description: .NET Framework, ADO.NET 'deki veri sağlayıcıları, verileri okumak ve güncelleştirmek için bir uygulamayla veri kaynağı arasında bir köprü olarak görev yapar.
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: f916324dc829526a5e6b0078021b09786755f666
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286617"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>ADO.NET’te Veri Alma ve Değiştirme
Herhangi bir veritabanı uygulamasının birincil işlevi bir veri kaynağına bağlanıyor ve içerdiği verileri alıyor. ADO.NET veri sağlayıcıları bir uygulama ile veri kaynağı arasında bir köprü olarak görev yapar ve ayrıca, bir **DataReader** veya **DataAdapter**kullanarak veri alma ve komutları yürütmenize olanak tanır. .NET Framework Herhangi bir veritabanı uygulamasının anahtar işlevi, veritabanında depolanan verileri güncelleştirebilme olanağıdır. ADO.NET ' de, verilerin güncelleştirilmesi **DataAdapter** ve <xref:System.Data.DataSet> **Command** nesnelerinin yanı sıra işlemleri kullanmayı da gerektirebilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bir veri kaynağına bağlanma](connecting-to-a-data-source.md)  
 Bir veri kaynağına nasıl bağlantı kurulacağını ve bağlantı olaylarıyla nasıl çalışabileceğinizi açıklar.  
  
 [Bağlantı dizeleri](connection-strings.md)  
 Bağlantı dizesi anahtar sözcükleri, güvenlik bilgileri ve bunları depolama ve alma gibi bağlantı dizelerini kullanmanın çeşitli yönlerini açıklayan konuları içerir.  
  
 [Bağlantı Havuzu](connection-pooling.md)  
 .NET Framework veri sağlayıcıları için bağlantı havuzunu açıklar.  
  
 [Komutlar ve Parametreler](commands-and-parameters.md)  
 Komutların ve komut oluşturucuların nasıl oluşturulacağını, parametrelerin nasıl yapılandırılacağını ve verilerin alınması ve değiştirilmesi için komutların nasıl yürütüleceğini açıklayan konuları içerir.  
  
 [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)  
 DataReaders, DataAdapter, Parameters, DataAdapter olaylarını işleme ve Batch işlemleri gerçekleştirme konularını açıklayan konuları içerir.  
  
 [İşlemler ve Eşzamanlılık](transactions-and-concurrency.md)  
 Yerel işlemlerin nasıl gerçekleştirileceğini, dağıtılmış işlemlerin ve iyimser eşzamanlılık ile nasıl çalıştığını açıklayan konuları içerir.  
  
 [Kimliği veya Otomatik Sayı Değerlerini Alma](retrieving-identity-or-autonumber-values.md)  
 Bir SQL Server tablosundaki bir **kimlik** sütunu için veya bir Microsoft Access tablosundaki bir **OtomatikSayı** alanı için oluşturulan değerleri bir tabloda bulunan satır sütunuyla eşlemek için bir örnek sağlar. İçindeki kimlik değerlerini birleştirmeyi açıklar `DataTable` .  
  
 [İkili Verileri Alma](retrieving-binary-data.md)  
 Kullanılarak ikili verilerin veya büyük veri yapılarının nasıl alınacağını açıklar `CommandBehavior` .`SequentialAccess` Varsayılan davranışını değiştirmek için `DataReader` .  
  
 [Saklı Yordamlarla Verileri Değiştirme](modifying-data-with-stored-procedures.md)  
 Yeni bir kimlik değeri döndüren bir veritabanına satır eklemek için saklı yordam giriş parametrelerinin ve çıkış parametrelerinin nasıl kullanılacağını açıklar.  
  
 [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)  
 Kullanılabilir veritabanlarının veya katalogların, tabloların ve görünümlerin bir veritabanında, tablolar için var olan kısıtlamaların ve bir veri kaynağından alınan diğer şema bilgilerinin nasıl alınacağını açıklar.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 Sağlayıcı fabrikası modelini açıklar ve ad alanındaki temel sınıfların nasıl kullanılacağını gösterir `System.Data.Common` .  
  
 [ADO.NET’te Veri İzleme](data-tracing.md)  
 ADO.NET 'in yerleşik veri izleme işlevselliği nasıl sağladığını açıklar.  
  
 [Performans sayaçları](performance-counters.md)  
 Ve için kullanılabilir performans sayaçlarını `SqlClient` açıklar `OracleClient` .  
  
 [Zaman uyumsuz programlama](asynchronous-programming.md)  
 Zaman uyumsuz programlama için ADO.NET desteğini açıklar.  
  
 [SqlClient Akış Desteği](sqlclient-streaming-support.md)  
 Verilerin belleğe tam olarak yüklenmesini gerektirmeden SQL Server veri akışı yapan uygulamaların nasıl yazılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Türü Eşlemeleri](data-type-mappings-in-ado-net.md)
- [DataSets, DataTables ve DataViews](./dataset-datatable-dataview/index.md)
- [ADO.NET Uygulamalarının Güvenliğini Sağlama](securing-ado-net-applications.md)
- [SQL Server ve ADO.NET](./sql/index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
