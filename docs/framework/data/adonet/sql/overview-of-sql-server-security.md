---
title: SQL Server Güvenliğine Genel Bakış
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: de0c79a95a786f33b05c88ce4ed298837f2a6923
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148596"
---
# <a name="overview-of-sql-server-security"></a>SQL Server Güvenliğine Genel Bakış
Güvenlik katmanları örtüşen derinlemesine savunma stratejisi, sayaç güvenlik tehditleri için en iyi yoludur. SQL Server veritabanı yöneticilerinin ve geliştiricilerin güvenli veritabanı uygulamaları ve sayaç tehditleri oluşturmak izin vermek için tasarlanmış bir güvenlik mimarisi sağlar. Her SQL Server sürümü, SQL Server'ın önceki sürümlerinde yeni özellikleri ve işlevleri tanıtımıyla geliştirdi. Ancak, güvenlik kutuya gelmez. Her uygulama, güvenlik gereksinimleri açısından benzersizdir. Geliştiriciler hangi özellik bileşimi anlamak gerekir ve işlevselliği için en uygun sayaç bilinen tehditlere ve gelecekte oluşabilecek tehditleri beklenir.  
  
 Bir SQL Server örneği ile sunucu başlangıç varlıkların hiyerarşik bir koleksiyonunu içerir. Her sunucu birden çok veritabanını, ve her veritabanı güvenliği sağlanabilir nesnelerin bir koleksiyonunu içerir. Güvenli kılınabilir her SQL Server ilişkili *izinleri* için verilebilir bir *asıl*, tek tek, bir grup olduğu veya SQL Server'a erişim verilen işlem. SQL Server güvenlik çerçevesi güvenli kılınabilir varlıklara erişimi yöneten *kimlik doğrulaması* ve *yetkilendirme*.  
  
-   Kimlik doğrulaması, SQL Server'ın kullandığı bir asıl sunucu değerlendiren kimlik bilgileri göndererek erişim isteğinde oturum açmadan işlemidir. Kimlik doğrulaması, kullanıcı veya kimlik doğrulaması gerçekleştirilen işlem kimliğini oluşturur.  
  
-   Yetkilendirme bir sorumluya erişmek güvenli kılınabilir kaynakları ve işlemleri için bu kaynakları izin belirleme işlemidir.  
  
 Bu bölümdeki konular, SQL Server güvenlik temelleri, SQL Server Books Online'nın ilgili sürümünde kapsamlı belgeler bağlantıları sağlayan kapsar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server’da Kimlik Doğrulaması](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 Oturum açma bilgileri ve SQL Server kimlik doğrulamasını açıklar ve ek kaynaklara bağlantılar sağlanmaktadır.  
  
 [SQL Server’da Sunucu ve Veritabanı Rolleri](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 Sabit sunucu ve veritabanı rolleri, özel veritabanı rolleri ve yerleşik hesaplar açıklar ve ek kaynaklara bağlantılar sağlanmaktadır.  
  
 [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 Nesne sahipliği ve kullanıcı şeması ayrımı açıklar ve ek kaynaklara bağlantılar sağlanmaktadır.  
  
 [SQL Server’da Yetkilendirme ve İzinler](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 En düşük öncelik ilkesini kullanarak izinleri açıklar ve ek kaynaklara bağlantılar sağlanmaktadır.  
  
 [SQL Server’da Veri Şifreleme](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 SQL Server'da veri şifreleme seçenekleri açıklar ve ek kaynaklara bağlantılar sağlanmaktadır.  
  
 [SQL Server’da CLR Tümleştirme Güvenliği](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 CLR tümleştirme güvenliği kaynaklarına bağlantılar sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server Güvenliği](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
