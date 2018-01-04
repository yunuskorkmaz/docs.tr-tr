---
title: '&#39; teki ADO.NET''deki yenilikler'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3944fb6d68ed054feb8d7ddec149745b78810ee2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="what39s-new-in-adonet"></a>&#39; teki ADO.NET'deki yenilikler
Aşağıdaki özellikleri yeni [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] içinde [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="sqlclient-data-provider"></a>SqlClient veri sağlayıcısı  
 Aşağıdaki özellikleri yeni [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] için veri sağlayıcı [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] içinde [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]:  
  
-   ConnectRetryCount ve ConnectRetryInterval bağlantı dizesi anahtar sözcükler (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) boştaki bağlantı dayanıklılığı özelliğini denetlemenize olanak verir.  
  
-   Destek'ten akış [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] bir uygulamaya veri sunucuda nerede yapılandırılmamış senaryolarını destekler.  Bkz: [SqlClient akış Destek](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md) daha fazla bilgi için.  
  
-   Zaman uyumsuz programlama için destek eklenmiştir.  Bkz: [zaman uyumsuz programlama](../../../../docs/framework/data/adonet/asynchronous-programming.md) daha fazla bilgi için.  
  
-   Bağlantı hataları artık genişletilmiş olay günlüğüne kaydedilir. Daha fazla bilgi için bkz: [veri izleme ADO.NET](../../../../docs/framework/data/adonet/data-tracing.md).  
  
-   SqlClient desteği artık sahiptir [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)]'s yüksek kullanılabilirlik, olağanüstü durum kurtarma özelliği, AlwaysOn. Daha fazla bilgi için bkz: [SqlClient yüksek kullanılabilirlik, olağanüstü durum kurtarma desteği](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).  
  
-   Parola olarak geçirilen bir <xref:System.Security.SecureString> kullanırken [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] kimlik doğrulaması. Daha fazla bilgi edinmek için bkz. <xref:System.Data.SqlClient.SqlCredential>.  
  
-   Zaman `TrustServerCertificate` false ve `Encrypt` true, sunucu adı (veya IP adresi) bulunduğu bir [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] SSL sertifikası sunucu adı (veya IP adresi) bağlantı dizesinde belirtilen tam olarak eşleşmelidir. Aksi takdirde, bağlantı girişimi başarısız olur. Daha fazla bilgi için açıklamasına bakın `Encrypt` bağlantı seçeneğinde <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
     Bu değişiklik artık bağlanmak var olan bir uygulama neden olursa, aşağıdakilerden birini kullanarak uygulamayı düzeltebilirsiniz:  
  
    -   Ortak ad (CN) veya konu alternatif adı (SAN) alanında kısa adı belirten bir sertifika verin. Bu çözüm, veritabanı yansıtma için çalışır.  
  
    -   Kısa adı tam etki alanı adıyla eşleşen bir diğer ad ekleyin.  
  
    -   Tam etki alanı adı bağlantı dizesinde kullanın.  
  
-   SqlClient genişletilmiş korumayı destekler. Genişletilmiş koruma hakkında daha fazla bilgi için bkz: [veritabanı altyapısı kullanarak genişletilmiş koruma için bağlanma](http://go.microsoft.com/fwlink/?LinkId=219978).  
  
-   SqlClient LocalDB veritabanlarına bağlantılarını destekler. Daha fazla bilgi için bkz: [LocalDB SqlClient desteği](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md).  
  
-   `Type System Version=SQL Server 2012;`geçirilecek yeni değer `Type System Version` bağlantı özelliği. `Type System Version=Latest;` Değer artık kullanımdan kalkmıştır ve eşdeğer yapılan `Type System Version=SQL Server 2008;`. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.  
  
-   SqlClient ek destek seyrek sütunlar için SQL Server 2008'de eklenen bir özelliği sağlar. Uygulama zaten bir seyrek sütun kullanan bir tablodaki verileri erişirse, performans artışı görmeniz gerekir. IsColumnSet sütunu <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> bir sütunu bir sütun kümesi üyesi olan bir seyrek sütun olup olmadığını gösterir. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>bir sütunu bir seyrek sütun olup olmadığını gösterir (bkz [SQL Server şeması koleksiyonları](../../../../docs/framework/data/adonet/sql-server-schema-collections.md) daha fazla bilgi için). Seyrek sütun hakkında daha fazla bilgi için bkz: [kullanarak seyrek sütun](http://go.microsoft.com/fwlink/?LinkId=224244).  
  
-   Uzamsal veri türleri içeriyor, Microsoft.SqlServer.Types.dll derleme sürüm 11.0 10.0 sürümünden yükseltildi. Bu derleme başvurusu uygulamalar başarısız olabilir. Daha fazla bilgi için bkz: [son değişiklikler için veritabanı altyapısı özelliklere](http://go.microsoft.com/fwlink/?LinkId=224367).  
  
## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework  
 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] Entity Framework 5.0 ile çalışırken, yeni senaryoları etkinleştirmek API'leri ekler. Geliştirmeleri ve Entity Framework 5.0 için eklenen özellikler hakkında daha fazla bilgi için aşağıdaki konulara bakın: [yenilikler](http://go.microsoft.com/fwlink/?LinkID=251106) ve [Entity Framework sürümleri ve sürüm oluşturma](http://go.microsoft.com/fwlink/?LinkId=234899).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET](../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)  
 [SQL Server ve ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [WCF Veri Hizmetleri yenilikleri](http://msdn.microsoft.com/en-us/cf22cad5-b8d9-472b-8d7c-b863b64eaae8)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
