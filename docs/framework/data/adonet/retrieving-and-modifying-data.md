---
title: Verileri alma ve değiştirme
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 65c373ecff004e219527754bf2e9cc56837dc305
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980060"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>ADO.NET’te Veri Alma ve Değiştirme
Herhangi bir veritabanı uygulamasının birincil işlevi bir veri kaynağına bağlanıyor ve içerdiği verileri alıyor. ADO.NET veri sağlayıcıları bir uygulama ile veri kaynağı arasında bir köprü olarak görev yapar ve ayrıca, bir **DataReader** veya **DataAdapter**kullanarak veri alma ve komutları yürütmenize olanak tanır. .NET Framework Herhangi bir veritabanı uygulamasının anahtar işlevi, veritabanında depolanan verileri güncelleştirebilme olanağıdır. ADO.NET ' de, verileri güncelleştirme, **DataAdapter** ve <xref:System.Data.DataSet>ile **komut** nesnelerinin kullanımı ile ilgilidir. Ayrıca işlem kullanmayı da gerektirebilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Veri Kaynağına Bağlanma](connecting-to-a-data-source.md)  
 Bir veri kaynağına nasıl bağlantı kurulacağını ve bağlantı olaylarıyla nasıl çalışabileceğinizi açıklar.  
  
 [Bağlantı Dizeleri](connection-strings.md)  
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
 Bir SQL Server tablosundaki bir **kimlik** sütunu için veya bir Microsoft Access tablosundaki bir **OtomatikSayı** alanı için oluşturulan değerleri bir tabloda bulunan satır sütunuyla eşlemek için bir örnek sağlar. Kimlik değerlerini bir `DataTable`birleştirmeyi açıklar.  
  
 [İkili Verileri Alma](retrieving-binary-data.md)  
 `CommandBehavior`kullanarak ikili verilerin veya büyük veri yapılarının nasıl alınacağını açıklar.`SequentialAccess` `DataReader`varsayılan davranışını değiştirmek için.  
  
 [Saklı Yordamlarla Verileri Değiştirme](modifying-data-with-stored-procedures.md)  
 Yeni bir kimlik değeri döndüren bir veritabanına satır eklemek için saklı yordam giriş parametrelerinin ve çıkış parametrelerinin nasıl kullanılacağını açıklar.  
  
 [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)  
 Kullanılabilir veritabanlarının veya katalogların, tabloların ve görünümlerin bir veritabanında, tablolar için var olan kısıtlamaların ve bir veri kaynağından alınan diğer şema bilgilerinin nasıl alınacağını açıklar.  
  
 [DbProviderFactories](dbproviderfactories.md)  
 Sağlayıcı fabrikası modelini açıklar ve `System.Data.Common` ad alanındaki temel sınıfların nasıl kullanılacağını gösterir.  
  
 [ADO.NET’te Veri İzleme](data-tracing.md)  
 ADO.NET 'in yerleşik veri izleme işlevselliği nasıl sağladığını açıklar.  
  
 [Performans Sayaçları](performance-counters.md)  
 `SqlClient` ve `OracleClient`için kullanılabilen performans sayaçlarını açıklar.  
  
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
