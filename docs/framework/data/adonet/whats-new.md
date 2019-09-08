---
title: ADO.NET’teki Yenilikler
ms.date: 03/30/2017
ms.assetid: 3bb65d38-cce2-46f5-b979-e5c505e95e10
ms.openlocfilehash: 0a02ca3885524c5fcf8def603acdce33a972d283
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791265"
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

- Parola, SQL Server kimlik doğrulaması kullanılırken bir <xref:System.Security.SecureString> olarak geçirilebilir. Daha fazla bilgi edinmek için bkz. <xref:System.Data.SqlClient.SqlCredential>.

- Yanlış olduğunda ve `Encrypt` doğru olduğunda, bir SQL Server SSL sertifikasındaki sunucu adı (veya IP adresi), bağlantı dizesinde belirtilen sunucu adı (veya IP adresi) ile tam olarak eşleşmelidir. `TrustServerCertificate` Aksi takdirde, bağlantı denemesi başarısız olur. Daha fazla bilgi için, `Encrypt` bağlantısındaki bağlantı <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>seçeneğinin açıklamasına bakın.

  Bu değişiklik, mevcut bir uygulamanın artık bağlanmasına neden olursa, aşağıdakilerden birini kullanarak uygulamayı çözebilirsiniz:

  - Ortak ad (CN) veya konu diğer adı (SAN) alanındaki kısa adı belirten bir sertifika verin. Bu çözüm, veritabanı yansıtma için çalışacaktır.

  - Kısa adı, tam etki alanı adına eşleyen bir diğer ad ekleyin.

  - Bağlantı dizesindeki tam etki alanı adını kullanın.

- SqlClient genişletilmiş korumayı destekler. Genişletilmiş koruma hakkında daha fazla bilgi için bkz. [genişletilmiş koruma kullanarak veritabanı altyapısına bağlanma](https://go.microsoft.com/fwlink/?LinkId=219978).

- SqlClient, LocalDB veritabanlarına bağlantıları destekler. Daha fazla bilgi için bkz. [LocalDB Için SqlClient desteği](./sql/sqlclient-support-for-localdb.md).

- `Type System Version=SQL Server 2012;`, `Type System Version` bağlantı özelliğine geçirilecek yeni bir değerdir. Değer artık kullanılmıyor ve ile `Type System Version=SQL Server 2008;`eşdeğer hale getirilir. `Type System Version=Latest;` Daha fazla bilgi için bkz. <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.

- SqlClient, SQL Server 2008 ' de eklenen bir özellik olan seyrek sütunlar için ek destek sağlar. Uygulamanız seyrek sütun kullanan bir tablodaki verilere zaten eriştiğinde performansta bir artış görmeniz gerekir. Icolumnset sütunu <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> , bir sütunun bir sütun kümesinin üyesi olan seyrek sütun olup olmadığını gösterir. <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A>bir sütunun seyrek sütun olup olmadığını gösterir (daha fazla bilgi için bkz. [SQL Server şeması koleksiyonları](sql-server-schema-collections.md) ). Seyrek sütunlar hakkında daha fazla bilgi için bkz. [seyrek sütun kullanımı](https://go.microsoft.com/fwlink/?LinkId=224244).

- Uzamsal veri türlerini içeren Microsoft. SqlServer. Types. dll derlemesi sürüm 10,0 ' den sürüm 11,0 ' den yükseltildi. Bu derlemeye başvuran uygulamalar başarısız olabilir. Daha fazla bilgi için bkz. [veritabanı altyapısı özelliklerine yönelik son değişiklikler](https://go.microsoft.com/fwlink/?LinkId=224367).

## <a name="adonet-entity-framework"></a>ADO.NET Entity Framework

.NET Framework 4,5, Entity Framework 5,0 ile çalışırken yeni senaryolar sağlayan API 'Ler ekler. 5,0 Entity Framework eklenen geliştirmeler ve özellikler hakkında daha fazla bilgi için aşağıdaki konulara bakın: [Yenilikler ve](https://go.microsoft.com/fwlink/?LinkID=251106) [Entity Framework sürümleri ve sürüm oluşturma](https://go.microsoft.com/fwlink/?LinkId=234899).

## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET](index.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
- [SQL Server ve ADO.NET](./sql/index.md)
- [WCF Veri Hizmetleri 5,0 ' deki yenilikler](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))
