---
title: ADO.NET’teki Yenilikler
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: 76ded71e7fa5ece382d0b0947eefa05682dc0f8e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673111"
---
# <a name="whats-new-in-adonet"></a>ADO.NET’teki Yenilikler

Aşağıdaki özellikleri yeni [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] içinde [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].

## <a name="sqlclient-data-provider"></a>SqlClient veri sağlayıcısı

Aşağıdaki özellikleri yeni [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SQL Server için veri sağlayıcısı [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]:

- ConnectRetryCount ve ConnectRetryInterval bağlantı dizesi anahtar sözcükleri (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>) boşta kalan bağlantı dayanıklılığı özelliğini denetlemenize olanak tanır.

- Akış desteği SQL Server'dan bir uygulamaya veri sunucuda yapılandırılmamış olduğu senaryolarını destekler.  Bkz: [SqlClient Streaming Support](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md) daha fazla bilgi için.

- Zaman uyumsuz programlama için destek eklendi.  Bkz: [Asynchronous Programming](../../../../docs/framework/data/adonet/asynchronous-programming.md) daha fazla bilgi için.

- Bağlantı hataları artık genişletilmiş olaylar günlüğe kaydedilir. Daha fazla bilgi için [ADO.NET'te veri izleme](../../../../docs/framework/data/adonet/data-tracing.md).

- SqlClient artık SQL Server'ın yüksek kullanılabilirlik, olağanüstü durum kurtarma özelliği, AlwaysOn desteği vardır. Daha fazla bilgi için [yüksek kullanılabilirlik, olağanüstü durum kurtarma için SqlClient desteği](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Bir parola olarak geçirilen bir <xref:System.Security.SecureString> SQL Server kimlik doğrulamasını kullanırken. Daha fazla bilgi edinmek için bkz. <xref:System.Data.SqlClient.SqlCredential>.

- Zaman `TrustServerCertificate` yanlış ve `Encrypt` bir SQL Server SSL sertifikasındaki sunucu adı (veya IP adresi) tam olarak eşleşmelidir sunucu adı (veya IP adresi) bağlantı dizesinde belirtilen true olur. Aksi takdirde, bağlantı denemesi başarısız olur. Daha fazla bilgi için açıklamasına bakın `Encrypt` bağlantı seçeneği <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

  Artık bağlanmak mevcut bir uygulama bu değişikliğin neden olursa, aşağıdakilerden birini kullanarak uygulamayı düzeltebilirsiniz:

  - Ortak ad (CN) veya konu alternatif adı (SAN) alanında kısa adını belirten bir sertifika vermek. Bu çözüm, veritabanı yansıtması için çalışır.

  - Kısa adı tam etki alanı adına eşleyen bir diğer ad ekleyin.

  - Tam etki alanı adını, bağlantı dizesini kullanın.

- Genişletilmiş Koruma SqlClient destekler. Genişletilmiş koruma hakkında daha fazla bilgi için bkz: [veritabanı altyapısı kullanılarak genişletilmiş koruma için bağlama](https://go.microsoft.com/fwlink/?LinkId=219978).

- SqlClient LocalDB veritabanlarına bağlantı destekler. Daha fazla bilgi için [LocalDB için SqlClient desteği](../../../../docs/framework/data/adonet/sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;` geçirmek için yeni değer `Type System Version` bağlantı özelliği. `Type System Version=Latest;` Değer artık kullanımdan kalkmıştır ve eşdeğer yapılan `Type System Version=SQL Server 2008;`. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- SqlClient, SQL Server 2008'de eklenen bir özelliği seyrek sütunlar için ek destek sağlar. Uygulamanız zaten bir seyrek sütun kullanan bir tablodaki verilere erişiyorsa, performans artışı görmeniz gerekir. IsColumnSet sütununun <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> sütunu bir sütun kümesi üyesi olan bir seyrek sütun olup olmadığını gösterir. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> bir sütunu bir seyrek sütun olup olmadığını gösterir (bkz [SQL Server şema koleksiyonları](../../../../docs/framework/data/adonet/sql-server-schema-collections.md) daha fazla bilgi için). Seyrek sütun hakkında daha fazla bilgi için bkz: [kullanarak bir seyrek sütun](https://go.microsoft.com/fwlink/?LinkId=224244).

- Uzamsal veri türleri içeren Microsoft.SqlServer.Types.dll derlemenin sürüm 11.0 10.0 sürümünden yükseltildi. Bu derlemeye başvuran uygulamalar başarısız olabilir. Daha fazla bilgi için [değişiklikler veritabanı altyapısı özellikleri](https://go.microsoft.com/fwlink/?LinkId=224367).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] Entity Framework 5.0 ile çalışırken yeni senaryolar sağlayan API'leri ekler. Geliştirmeleri ve Entity Framework 5.0 eklenen özellikler hakkında daha fazla bilgi için aşağıdaki konulara bakın: [Yenilikler](https://go.microsoft.com/fwlink/?LinkID=251106) ve [Entity Framework sürümleri ve sürüm oluşturma](https://go.microsoft.com/fwlink/?LinkId=234899).

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](../../../../docs/framework/data/adonet/index.md)
- [ADO.NET’e Genel Bakış](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [SQL Server ve ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)
- [WCF Veri Hizmetleri 5.0 yenilikler nelerdir?](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
