---
title: Alma ve ADO.NET veri değiştirme
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 0c970c01352aecf6a25bac1b89b9f79c96f80d31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361549"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Alma ve ADO.NET veri değiştirme
Birincil işlev herhangi bir veritabanı uygulamasını bir veri kaynağına bağlanma ve içerdiği veriler alınıyor. Kullanarak veri almak için de komutları yürütün olanak tanıyan bir uygulama ile bir veri kaynağı arasında bir köprü olarak ADO .NET Framework veri sağlayıcıları hizmet bir **DataReader** veya **DataAdapter** . Bir anahtar herhangi bir veritabanı uygulamasını veritabanında depolanan veri güncelleştirme becerisini işlevdir. ADO.NET, verileri güncelleştirme kullanılmasına **DataAdapter** ve <xref:System.Data.DataSet>, ve **komutu** nesneleri; ve bu da gerektirebilir işlemleri kullanma.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 Bir veri kaynağı bağlantı kurmak ve bağlantı olayları ile çalışmak açıklar.  
  
 [Bağlantı Dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)  
 Bağlantı dizeleri kullanılarak, bağlantı dizesi anahtar sözcükler, güvenlik bilgileri de dahil olmak üzere ve depolamak ve bunlara alma çeşitli yönlerini açıklayan konuları içerir.  
  
 [Bağlantı Havuzu](../../../../docs/framework/data/adonet/connection-pooling.md)  
 .NET Framework veri sağlayıcıları için bağlantı havuzunu açıklar.  
  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 Komutları ve komut oluşturucular oluşturma, parametreleri yapılandırmak ve almak ve veri değiştirmek için komutları yürütmek nasıl açıklayan konuları içerir.  
  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 Açıklayan DataReader, DataAdapters, parametreleri, olaylarını işleme ve toplu işlemleri konuları içerir.  
  
 [İşlemler ve Eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 Yerel işlemler, dağıtılmış işlemler gerçekleştirmek ve iyimser eşzamanlılık ile çalışmak nasıl açıklayan konuları içerir.  
  
 [Kimliği veya Otomatik Sayı Değerlerini Alma](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 İçin oluşturulan değerler eşleme örneğidir bir **kimlik** sütun için veya bir SQL Server tablosundaki bir **sayı** eklenen bir satırın bir tablodaki bir sütun için bir Microsoft Access tablosundaki. Birleştirme kimlik değerleri açıklanır bir `DataTable`.  
  
 [İkili Verileri Alma](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 İkili veriler veya kullanarak büyük veri yapıları almak açıklar `CommandBehavior`.`SequentialAccess` varsayılan davranışını değiştirmek için bir `DataReader`.  
  
 [Saklı Yordamlarla Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 Saklı yordam giriş parametreleri ve yeni bir kimlik değeri döndüren bir veritabanında, satır ekleme parametreleri çıktı nasıl kullanılacağı açıklanmaktadır.  
  
 [Veritabanı Şema Bilgilerini Alma](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 Kullanılabilir veritabanları ya da kataloglar, tablolar ve görünümler bir veritabanı tablolar ve veri kaynağındaki diğer şema bilgileri için mevcut kısıtlamaları alma yolları açıklanır.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Sağlayıcı fabrikası modeli açıklar ve temel sınıflarda kullanımı gösterilmiştir `System.Data.Common` ad alanı.  
  
 [ADO.NET’te Veri İzleme](../../../../docs/framework/data/adonet/data-tracing.md)  
 ADO.NET yerleşik veri izleme işlevselliği nasıl sağladığını açıklar.  
  
 [Performans Sayaçları](../../../../docs/framework/data/adonet/performance-counters.md)  
 Performans sayaçları için kullanılabilir açıklar `SqlClient` ve `OracleClient`.  
  
 [Zaman uyumsuz programlama](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 Açıklar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zaman uyumsuz programlama desteği.  
  
 [SqlClient Akış Desteği](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 Uygulamaların veri akışı SQL Server'dan onu tam olarak belleğe yüklenen gerek kalmadan nasıl yazılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server ve ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
