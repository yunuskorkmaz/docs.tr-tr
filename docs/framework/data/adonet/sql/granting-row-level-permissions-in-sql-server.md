---
title: SQL Server’da Satır Düzeyinde İzinler Verme
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: df5fcb4a6c73e12bec2ab17501fdfb02cf672324
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782358"
---
# <a name="granting-row-level-permissions-in-sql-server"></a>SQL Server’da Satır Düzeyinde İzinler Verme

Bazı senaryolarda verilere erişimi daha ayrıntılı bir düzeyde denetlemek, izinlerin sağlanması, iptal edilmesinin veya reddetmesinin sağladığı bir gereksinimdir. Örneğin, bir barındırma veritabanı uygulaması, tek tek her bir Doctors 'ın yalnızca kendi hastalarıyla ilgili bilgilere erişmesine izin verebilir. Finans, hukuk, devlet ve askeri uygulamalar dahil olmak üzere birçok ortamda benzer gereksinimler mevcuttur. SQL Server 2016, bu senaryolara yardımcı olmak için, bir güvenlik ilkesinde satır düzeyi erişim mantığını basitleştiren ve merkezileştiren bir [satır düzeyi güvenlik](/sql/relational-databases/security/row-level-security) özelliği sağlar. Daha önceki SQL Server sürümleri için, satır düzeyinde filtrelemeyi uygulamak üzere görünümler kullanılarak benzer işlevler elde edilebilir.

## <a name="implementing-row-level-filtering"></a>Satır düzeyinde filtreleme uygulama

Satır düzeyinde filtreleme, yukarıdaki barındırma örneğinde olduğu gibi tek bir tabloda bilgi depolayan uygulamalar için kullanılır. Satır düzeyinde filtreleme uygulamak için her satırda bir Kullanıcı adı, etiket veya başka bir tanımlayıcı gibi bir ayrım parametresi tanımlayan bir sütun bulunur. Bir güvenlik ilkesi veya tabloda, kullanıcının erişebileceği satırları filtreleyen bir görünüm oluşturursunuz. Ardından, kullanıcının yürütebileceği sorgu türlerini denetleyen parametreli saklı yordamlar oluşturursunuz.

Aşağıdaki örnek, bir kullanıcı veya oturum açma adına göre satır düzeyinde filtrelemenin nasıl yapılandırılacağını açıklar:

- Adı depolamak için bir sütun ekleyerek tablo oluşturun.

- Satır düzeyinde filtrelemeyi etkinleştir:

  - SQL Server 2016 veya üzeri ya da [Azure SQL veritabanı](https://docs.microsoft.com/azure/sql-database/)kullanıyorsanız, geçerli veritabanı kullanıcısı ile eşleşen satırları kısıtlayan tabloya bir koşul ekleyen bir güvenlik ilkesi oluşturun (CURRENT_USER () yerleşik işlevini kullanarak) veya geçerli oturum açma adı (SUSER_SNAME () yerleşik işlevini kullanarak):

      ```sql
      CREATE SCHEMA Security
      GO

      CREATE FUNCTION Security.userAccessPredicate(@UserName sysname)
          RETURNS TABLE
          WITH SCHEMABINDING
      AS
          RETURN SELECT 1 AS accessResult
          WHERE @UserName = SUSER_SNAME()
      GO

      CREATE SECURITY POLICY Security.userAccessPolicy
          ADD FILTER PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable,
          ADD BLOCK PREDICATE Security.userAccessPredicate(UserName) ON dbo.MyTable
      GO
      ```

  - 2016 ' den önceki bir SQL Server sürümünü kullanıyorsanız, bir görünümü kullanarak benzer işlevlere ulaşabilirsiniz:

      ```sql
      CREATE VIEW vw_MyTable
      AS
          RETURN SELECT * FROM MyTable
          WHERE UserName = SUSER_SNAME()
      GO
      ```

- Verileri seçmek, eklemek, güncelleştirmek ve silmek için saklı yordamlar oluşturun. Filtreleme bir güvenlik ilkesiyle çalışıyorsa, saklı yordamlar bu işlemleri doğrudan temel tabloda gerçekleştirmelidir; Aksi takdirde, filtreleme bir görünüm tarafından işlem halinde kullanılıyorsa, saklı yordamlar bu görünümde bunun yerine çalışır. Güvenlik ilkesi veya görünümü, Kullanıcı sorguları tarafından döndürülen veya değiştirilen satırları otomatik olarak filtreleyecek ve saklı yordam, kullanıcıların bir şekilde, filtrelenmiş verilerin varlığı.

- Veri ekleyen saklı yordamlar için, güvenlik ilkesinde veya görünümünde belirtilen işlevi kullanarak Kullanıcı adını yakalayın ve bu değeri Kullanıcı adı sütununa ekleyin.

- `public` Roldeki tablolardaki (ve varsa görünümler) tüm izinleri reddedin. Filtre koşulu, rollere değil Kullanıcı veya oturum açma adlarını temel aldığı için kullanıcılar diğer veritabanı rollerinden izinleri devralmasını mümkün olmayacaktır.

- Saklı yordamlarda veritabanı rollerine yürütme izni verin. Kullanıcılar verilere yalnızca belirtilen saklı yordamlar aracılığıyla erişebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Satır düzeyi güvenlik](/sql/relational-databases/security/row-level-security)
- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server Güvenliğine Genel Bakış](overview-of-sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [SQL Server'da Saklı Yordam İzinlerini Yönetme](managing-permissions-with-stored-procedures-in-sql-server.md)
- [SQL Server’da Secure Dynamic SQL Yazma](writing-secure-dynamic-sql-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
