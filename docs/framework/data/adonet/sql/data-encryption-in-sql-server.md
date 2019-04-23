---
title: SQL Server’da Veri Şifreleme
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: 1acb720b8a4f8beb27bb1a5236efdb6f2bb44383
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102173"
---
# <a name="data-encryption-in-sql-server"></a>SQL Server’da Veri Şifreleme
SQL Server şifrelemek ve bir sertifika, asimetrik anahtar veya simetrik anahtar kullanarak verilerin şifresini çözmek için işlevler sağlar. Tüm bunların bir iç sertifika deposunda yönetir. Depolama ve sertifikaları anahtarlar üzerindeki katman hiyerarşideki bir düzeyde bir şifreleme hiyerarşisi kullanır. Bu özellik alanı SQL Server'ın, gizli depolama olarak adlandırılır.  
  
 Hızlı şifreleme işlevleri tarafından desteklenen şifreleme simetrik anahtar şifreleme modudur. Bu mod, büyük miktarda veriyi işlemek için uygundur. Simetrik anahtarlar, sertifikalar, parolalar veya diğer simetrik anahtarlar tarafından şifrelenebilir.  
  
## <a name="keys-and-algorithms"></a>Anahtarlar ve algoritmaları  
 SQL Server, DES, Üçlü DES, RC2, RC4, 128 bit RC4'ü, DESX, 128 bit AES, 192 bitlik AES ve 256 bit AES dahil olmak üzere çeşitli simetrik anahtar şifreleme algoritmalarını destekler. Windows şifreleme API'si günlük kaydını kullanarak algoritmalar uygulanır.  
  
 Veritabanı bağlantısı kapsamında, SQL Server birden fazla açık simetrik anahtarları koruyabilir. Açık bir anahtarı deposundan alınır ve verilerin şifresini çözmek için kullanılabilir. Bir veri parçasını şifresi, simetrik anahtarı belirtmek için gerek yoktur. Her bir şifrelenmiş değer anahtarı içeren cihazı şifrelemek için kullanılan anahtarı tanımlayıcısı (GUID anahtar). Doğru anahtar şifresi çözüldükten ve açıksa açık bir simetrik anahtarı için şifrelenmiş bayt akışı altyapısı eşleşir. Bu anahtar ardından şifre çözme gerçekleştirebilir ve verileri döndürmek için kullanılır. Doğru anahtarı açık değilse null değeri döndürülür.  
  
 Veritabanındaki şifrelenmiş veriler ile nasıl çalışılacağını gösteren bir örnek için bkz: [bir veri sütununu şifreleme](/sql/relational-databases/security/encryption/encrypt-a-column-of-data).
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Veri şifreleme hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|-|-|  
|[SQL Server şifreleme](/sql/relational-databases/security/encryption/sql-server-encryption)|SQL Server şifreleme genel bir bakış sağlar. Bu konu, ek makalelere bağlantılar içerir.|  
|[Şifreleme hiyerarşisi](/sql/relational-databases/security/encryption/encryption-hierarchy)|SQL Server şifreleme genel bir bakış sağlar. Bu konu, ek makalelere bağlantılar sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server’da Kimlik Doğrulaması](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)
- [SQL Server’da Sunucu ve Veritabanı Rolleri](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)
- [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)
- [SQL Server’da Yetkilendirme ve İzinler](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
