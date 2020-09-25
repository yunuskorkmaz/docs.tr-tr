---
title: SQL Server’da Veri Şifreleme
ms.date: 03/30/2017
ms.assetid: 83b992f7-b351-4678-b4b9-f4ffd58134cc
ms.openlocfilehash: d0bda11f1a2933d096aa91d2be79d3af35172284
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169537"
---
# <a name="data-encryption-in-sql-server"></a>SQL Server’da Veri Şifreleme

SQL Server, bir sertifika, asimetrik anahtar veya simetrik anahtar kullanarak verileri şifrelemek ve şifrelerini çözmek için işlevler sağlar. Bunların hepsini bir iç sertifika deposunda yönetir. Mağaza, bir düzeydeki sertifikaları ve anahtarları hiyerarşide üzerinde bulunan katmanla aynı düzeyde güvenlik altına alan bir şifreleme hiyerarşisi kullanır. SQL Server bu özellik alanı gizli depolama olarak adlandırılır.  
  
 Şifreleme işlevlerinin desteklediği en hızlı şifreleme modu simetrik anahtar şifrelemedir. Bu mod, büyük hacimde veri işlemeye uygundur. Simetrik anahtarlar sertifikalarla, parolalarla veya diğer simetrik anahtarlarla şifrelenebilir.  
  
## <a name="keys-and-algorithms"></a>Anahtarlar ve algoritmalar  

 SQL Server DES, Üçlü DES, RC2, RC4, 128-bit RC4, DESX, 128-bit AES, 192 bit AES ve 256 bit AES dahil olmak üzere birkaç simetrik anahtar şifreleme algoritmasını destekler. Algoritmalar Windows şifreleme API 'SI kullanılarak uygulanır.  
  
 Bir veritabanı bağlantısının kapsamında, SQL Server birden çok açık simetrik anahtar tutabilir. Mağazadan bir açık anahtar alınır ve verilerin şifresini çözmek için kullanılabilir. Veri parçasının şifresi çözülemediğinden, kullanılacak simetrik anahtarı belirtmeniz gerekmez. Her şifreli değer, şifrelemek için kullanılan anahtarın anahtar tanımlayıcısını (anahtar GUID) içerir. Doğru anahtarın şifresi çözülediyse ve açıksa, motor şifreli bayt akışıyla açık bir simetrik anahtarla eşleşir. Bu anahtar daha sonra şifre çözme gerçekleştirmek ve verileri döndürmek için kullanılır. Doğru anahtar açık değilse NULL döndürülür.  
  
 Bir veritabanında şifreli verilerle çalışmayı gösteren bir örnek için bkz. [veri sütununu şifreleme](/sql/relational-databases/security/encryption/encrypt-a-column-of-data).
  
## <a name="external-resources"></a>Dış Kaynaklar  

 Veri şifreleme hakkında daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|-|-|  
|[SQL Server şifreleme](/sql/relational-databases/security/encryption/sql-server-encryption)|SQL Server 'de şifrelemeye genel bakış sağlar. Bu konu, ek makalelerin bağlantılarını içerir.|  
|[Şifreleme hiyerarşisi](/sql/relational-databases/security/encryption/encryption-hierarchy)|SQL Server 'de şifrelemeye genel bakış sağlar. Bu konu, ek makalelere bağlantılar sağlar.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [SQL Server’da Kimlik Doğrulaması](authentication-in-sql-server.md)
- [SQL Server’da Sunucu ve Veritabanı Rolleri](server-and-database-roles-in-sql-server.md)
- [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](ownership-and-user-schema-separation-in-sql-server.md)
- [SQL Server’da Yetkilendirme ve İzinler](authorization-and-permissions-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
