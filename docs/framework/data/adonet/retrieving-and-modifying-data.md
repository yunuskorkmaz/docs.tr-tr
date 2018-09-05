---
title: Alma ve ADO.NET veri değiştirme
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 5ef5191cf89f22fbaf0bb1bf4fbf47db1d4c06a1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43562569"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Alma ve ADO.NET veri değiştirme
Herhangi bir veritabanı uygulama birincil işlevi bir veri kaynağına bağlanmak ve içerdiği veriler alınıyor. ADO.NET, .NET Framework veri sağlayıcıları kullanarak veri almak için de komutları yürütmek olanak tanıyan bir uygulama ve bir veri kaynağı arasında bir köprü olarak hizmet verecek bir **DataReader** veya **DataAdapter** . Herhangi bir veritabanı uygulama anahtar işlevi veritabanında depolanan verileri güncelleştirmek için olanağıdır. ADO.NET ile veri güncelleştirme kullanılmasına **DataAdapter** ve <xref:System.Data.DataSet>, ve **komut** nesneler; ve bu da gerektirebilir işlemleri kullanma.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 Nasıl bir veri kaynağına bağlantı kurmak ve bağlantı olayları ile çalışma konusunda açıklanmaktadır.  
  
 [Bağlantı Dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)  
 Bağlantı dizeleri kullanarak, bağlantı dizesi anahtar sözcükler, güvenlik bilgileri de dahil olmak üzere ve depolamak ve bunları almak çeşitli yönlerini açıklayan konuları içerir.  
  
 [Bağlantı Havuzu](../../../../docs/framework/data/adonet/connection-pooling.md)  
 .NET Framework veri sağlayıcıları için bağlantı havuzu açıklar.  
  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 Komutlar ve komut oluşturucular oluşturma parametreleri yapılandırmak nasıl ve almak ve verileri değiştirmek için komutları yürütmek nasıl eklendiğini açıklayan konulara içerir.  
  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 DataReader, DataAdapters parametrelerini açıklayan, DataAdapter olaylarını işleme ve toplu işlemleri gerçekleştirme konuları içerir.  
  
 [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 Yerel işlemler, dağıtılmış işlemler gerçekleştirmek ve iyimser eşzamanlılık ile çalışmak nasıl eklendiğini açıklayan konulara içerir.  
  
 [Kimliği veya Otomatik Sayı Değerlerini Alma](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 Eşleme için oluşturulan değerleri bir örnek sağlar bir **kimlik** için bir SQL Server tablo veya sütun bir **sayı** tablodaki eklenen bir satır içeren bir sütun için bir Microsoft Access tablosundaki. Birleştirme kimlik değerleri açıklar bir `DataTable`.  
  
 [İkili Verileri Alma](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 İkili verileri veya büyük veri yapılarını kullanarak alınacak açıklar `CommandBehavior`.`SequentialAccess` varsayılan davranışını değiştirmek için bir `DataReader`.  
  
 [Saklı Yordamlarla Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 Saklı yordam giriş parametreleri ve çıkış parametreleri bir veritabanında yeni bir kimlik değeri döndüren bir satır eklemek için nasıl kullanılacağını açıklar.  
  
 [Veritabanı Şema Bilgilerini Alma](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 Kullanılabilir veritabanlarını veya kataloglar, tabloları ve görünümleri bir veritabanındaki tabloları ve diğer şema bilgileri bir veri kaynağından mevcut kısıtlamalar alma yolları açıklanır.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Sağlayıcı fabrikası modelini açıklar ve taban sınıflardaki kullanmayı gösteren `System.Data.Common` ad alanı.  
  
 [ADO.NET’te Veri İzleme](../../../../docs/framework/data/adonet/data-tracing.md)  
 ADO.NET veri yerleşik izleme işlevselliği nasıl sağladığını açıklar.  
  
 [Performans Sayaçları](../../../../docs/framework/data/adonet/performance-counters.md)  
 İçin kullanılabilen performans sayaçlarının açıklar `SqlClient` ve `OracleClient`.  
  
 [Zaman uyumsuz programlama](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 Açıklar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zaman uyumsuz programlama için destek.  
  
 [SqlClient Akış Desteği](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 SQL Server'dan veri akışı, tam olarak belleğe zorunda kalmadan uygulamaları yazmak nasıl ele alınmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server ve ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
