---
title: Yenilikler
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: 2ac8ebced700dc6c874ac22304773b3b9c19f8b3
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979764"
---
# <a name="whats-new-in-adonet"></a>ADO.NET’teki Yenilikler

Aşağıdaki özellikler .NET Framework 4,5 ' de yeni ADO.NET.

## <a name="sqlclient-data-provider"></a>SqlClient Veri Sağlayıcısı

Aşağıdaki özellikler .NET Framework 4,5 ' de SQL Server için .NET Framework Veri Sağlayıcısı yenidir:

- ConnectRetryCount ve ConnectRetryInterval bağlantı dizesi anahtar sözcükleri (<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>), boştaki bağlantı dayanıklılığı özelliğini denetlemenizi sağlar.

- SQL Server bir uygulamaya akış desteği, sunucudaki verilerin yapılandırılmamış olduğu senaryoları destekler.  Daha fazla bilgi için bkz. [SqlClient akış desteği](sqlclient-streaming-support.md) .

- Zaman uyumsuz programlama için destek eklenmiştir.  Daha fazla bilgi için bkz. [zaman uyumsuz programlama](asynchronous-programming.md) .

- Bağlantı hatalarıyla artık genişletilmiş olaylar günlüğüne kaydedilecek. Daha fazla bilgi için bkz. [ADO.net 'de veri izleme](data-tracing.md).

- SqlClient artık SQL Server yüksek kullanılabilirlik, olağanüstü durum kurtarma özelliği, AlwaysOn desteğine sahiptir. Daha fazla bilgi için bkz. [yüksek kullanılabilirlik Için SqlClient desteği, olağanüstü durum kurtarma](./sql/sqlclient-support-for-high-availability-disaster-recovery.md).

- Bir parola, SQL Server kimlik doğrulaması kullanılırken <xref:System.Security.SecureString> olarak geçirilebilir. Daha fazla bilgi edinmek için bkz. <xref:System.Data.SqlClient.SqlCredential>.

- `TrustServerCertificate` false olduğunda ve `Encrypt` doğru olduğunda, bir SQL Server SSL sertifikasındaki sunucu adı (veya IP adresi), bağlantı dizesinde belirtilen sunucu adı (veya IP adresi) ile tam olarak eşleşmelidir. Aksi takdirde, bağlantı denemesi başarısız olur. Daha fazla bilgi için <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>`Encrypt` bağlantı seçeneğinin açıklamasına bakın.

  Bu değişiklik, mevcut bir uygulamanın artık bağlanmasına neden olursa, aşağıdakilerden birini kullanarak uygulamayı çözebilirsiniz:

  - Ortak ad (CN) veya konu diğer adı (SAN) alanındaki kısa adı belirten bir sertifika verin. Bu çözüm, veritabanı yansıtma için çalışacaktır.

  - Kısa adı, tam etki alanı adına eşleyen bir diğer ad ekleyin.

  - Bağlantı dizesindeki tam etki alanı adını kullanın.

- SqlClient genişletilmiş korumayı destekler. Genişletilmiş koruma hakkında daha fazla bilgi için bkz. [genişletilmiş koruma kullanarak veritabanı altyapısına bağlanma](/sql/database-engine/configure-windows/connect-to-the-database-engine-using-extended-protection).

- SqlClient, LocalDB veritabanlarına bağlantıları destekler. Daha fazla bilgi için bkz. [LocalDB Için SqlClient desteği](./sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;`, `Type System Version` Connection özelliğine geçirilecek yeni bir değerdir. `Type System Version=Latest;` değeri artık kullanımdan kaldırılmıştır ve `Type System Version=SQL Server 2008;`eşdeğer hale getirilir. Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- SqlClient, SQL Server 2008 ' de eklenen bir özellik olan seyrek sütunlar için ek destek sağlar. Uygulamanız seyrek sütun kullanan bir tablodaki verilere zaten eriştiğinde performansta bir artış görmeniz gerekir. <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> IsColumnSet sütunu, bir sütunun bir sütun kümesinin üyesi olan seyrek sütun olup olmadığını gösterir. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> bir sütunun seyrek sütun olup olmadığını gösterir (daha fazla bilgi için bkz. [SQL Server şema koleksiyonlarına](sql-server-schema-collections.md) bakın). Seyrek sütunlar hakkında daha fazla bilgi için bkz. [seyrek sütun kullanma](/sql/relational-databases/tables/use-sparse-columns).

- Uzamsal veri türlerini içeren Microsoft. SqlServer. Types. dll derlemesi sürüm 10,0 ' den sürüm 11,0 ' den yükseltildi. Bu derlemeye başvuran uygulamalar başarısız olabilir. Daha fazla bilgi için bkz. [veritabanı altyapısı özelliklerine yönelik son değişiklikler](https://docs.microsoft.com/previous-versions/sql/sql-server-2012/ms143179(v=sql.110)).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

.NET Framework 4,5, Entity Framework 5,0 ile çalışırken yeni senaryolar sağlayan API 'Ler ekler. 5,0 Entity Framework eklenen geliştirmeler ve özellikler hakkında daha fazla bilgi için, şu konulara [bakın: yenilikler](https://docs.microsoft.com/previous-versions/gg696190(v=vs.103)) ve [Entity Framework sürümleri ve sürüm oluşturma](/ef/ef6/what-is-new/past-releases).

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
- [SQL Server ve ADO.NET](./sql/index.md)
- [WCF Veri Hizmetleri 5,0 ' deki yenilikler](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
