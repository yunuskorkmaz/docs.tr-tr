---
title: "Alma ve ADO.NET veri değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 35de20b1cb35fdcd87a653f1ac202c01d345c317
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>Alma ve ADO.NET veri değiştirme
Birincil işlev herhangi bir veritabanı uygulamasını bir veri kaynağına bağlanma ve içerdiği veriler alınıyor. Kullanarak veri almak için de komutları yürütün olanak tanıyan bir uygulama ile bir veri kaynağı arasında bir köprü olarak ADO .NET Framework veri sağlayıcıları hizmet bir **DataReader** veya **DataAdapter** . Bir anahtar herhangi bir veritabanı uygulamasını veritabanında depolanan veri güncelleştirme becerisini işlevdir. ADO.NET, verileri güncelleştirme kullanılmasına **DataAdapter** ve <xref:System.Data.DataSet>, ve **komutu** nesneleri; ve bu da gerektirebilir işlemleri kullanma.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bir veri kaynağına bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 Bir veri kaynağı bağlantı kurmak ve bağlantı olayları ile çalışmak açıklar.  
  
 [Bağlantı dizeleri](../../../../docs/framework/data/adonet/connection-strings.md)  
 Bağlantı dizeleri kullanılarak, bağlantı dizesi anahtar sözcükler, güvenlik bilgileri de dahil olmak üzere ve depolamak ve bunlara alma çeşitli yönlerini açıklayan konuları içerir.  
  
 [Bağlantı havuzu](../../../../docs/framework/data/adonet/connection-pooling.md)  
 .NET Framework veri sağlayıcıları için bağlantı havuzunu açıklar.  
  
 [Komutları ve parametreleri](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 Komutları ve komut oluşturucular oluşturma, parametreleri yapılandırmak ve almak ve veri değiştirmek için komutları yürütmek nasıl açıklayan konuları içerir.  
  
 [DataAdapters ve DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 Açıklayan DataReader, DataAdapters, parametreleri, olaylarını işleme ve toplu işlemleri konuları içerir.  
  
 [İşlemler ve eşzamanlılık](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 Yerel işlemler, dağıtılmış işlemler gerçekleştirmek ve iyimser eşzamanlılık ile çalışmak nasıl açıklayan konuları içerir.  
  
 [Kimliği veya sayı değerlerini alma](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 İçin oluşturulan değerler eşleme örneğidir bir **kimlik** sütununda bir [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] tablo veya bir **sayı** eklenen bir satırın bir tablodaki bir sütun için bir Microsoft Access tablosundaki. Birleştirme kimlik değerleri açıklanır bir `DataTable`.  
  
 [İkili veriler alınıyor](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 İkili veriler veya kullanarak büyük veri yapıları almak açıklar `CommandBehavior`.`SequentialAccess` varsayılan davranışını değiştirmek için bir `DataReader`.  
  
 [Saklı yordamlar verilerle değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 Saklı yordam giriş parametreleri ve yeni bir kimlik değeri döndüren bir veritabanında, satır ekleme parametreleri çıktı nasıl kullanılacağı açıklanmaktadır.  
  
 [Veritabanı şema bilgileri alınıyor](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 Kullanılabilir veritabanları ya da kataloglar, tablolar ve görünümler bir veritabanı tablolar ve veri kaynağındaki diğer şema bilgileri için mevcut kısıtlamaları alma yolları açıklanır.  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 Sağlayıcı fabrikası modeli açıklar ve temel sınıflarda kullanımı gösterilmiştir `System.Data.Common` ad alanı.  
  
 [ADO.NET veri izleme](../../../../docs/framework/data/adonet/data-tracing.md)  
 ADO.NET yerleşik veri izleme işlevselliği nasıl sağladığını açıklar.  
  
 [Performans sayaçları](../../../../docs/framework/data/adonet/performance-counters.md)  
 Performans sayaçları için kullanılabilir açıklar `SqlClient` ve `OracleClient`.  
  
 [Zaman uyumsuz programlama](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 Açıklar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zaman uyumsuz programlama desteği.  
  
 [SqlClient akış desteği](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 Veri akış uygulamaları nasıl yazılacağından [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] gerek kalmadan tam olarak bellekte yüklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET veri türü eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [Veri kümeleri, DataTable ve DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server ve ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
