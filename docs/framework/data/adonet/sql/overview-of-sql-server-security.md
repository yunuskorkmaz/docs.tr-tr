---
title: SQL Server güvenlik genel bakış
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: 84b6724417d03a30c131700e197744839d3a020d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="overview-of-sql-server-security"></a>SQL Server güvenlik genel bakış
Güvenlik, katmanları çakışan bir savunma stratejisi, sayaç güvenlik tehditleri için en iyi yoludur. SQL Server veritabanı Yöneticiler ve geliştiriciler güvenli veritabanı uygulamaları ve sayaç tehditlere oluşturmak izin vermek için tasarlanmış bir güvenlik mimarisi sağlar. Her SQL Server sürümü, SQL Server'ın önceki sürümlerinde kullanıma sunulması, yeni özellikler ve işlevsellik ile geliştirilmiştir. Ancak, güvenlik kutusuna gelmez. Her uygulama, güvenlik gereksinimleri açısından benzersizdir. Geliştiriciler hangi özellik bileşimi anlamak gerekir ve işlevselliği için en uygun sayaç bilinen tehditlere ve gelecekte kaynaklanabilecek tehditleri tahmin etmenize.  
  
 Bir SQL Server örneği sunucuyla başlama varlıklar, hiyerarşik bir koleksiyonunu içerir. Birden çok veritabanı her sunucuyu içerir ve her veritabanı güvenliği sağlanabilir nesneler koleksiyonunu içerir. Güvenli kılınabilir her SQL Server ilişkili *izinleri* , olanağı verilir bir *asıl*, bir kişi, Grup olduğu veya SQL Server'a erişim verilen işlem. SQL Server güvenlik çerçevesi güvenliği sağlanabilir varlıklara erişimi yöneten *kimlik doğrulaması* ve *yetkilendirme*.  
  
-   Kimlik doğrulaması olarak bir asıl sunucusu değerlendirir kimlik bilgileri göndererek erişim isteğinde SQL Server'da oturum açmayı işlemidir. Kimlik doğrulaması kullanıcı veya kimlik doğrulaması gerçekleştirilen işlem kimliği oluşturur.  
  
-   Yetkilendirme sorumlu erişmek için hangi güvenliği sağlanabilir kaynakları ve işlemleri kaynaklarla için izin verilen belirleme işlemidir.  
  
 Bu bölümdeki konular, SQL Server, SQL Server Books Online'nın ilgili sürümünde kapsamlı belgeler bağlantılar sağlayan güvenlik temelleri kapsar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [SQL Server’da Kimlik Doğrulaması](../../../../../docs/framework/data/adonet/sql/authentication-in-sql-server.md)  
 Oturum açma bilgileri ve SQL Server kimlik doğrulaması açıklanmakta ve ek kaynaklara bağlantılar sağlanmaktadır.  
  
 [SQL Server’da Sunucu ve Veritabanı Rolleri](../../../../../docs/framework/data/adonet/sql/server-and-database-roles-in-sql-server.md)  
 Sabit sunucu ve veritabanı rolleri, özel veritabanı rolleri ve yerleşik hesapları açıklanmakta ve ek kaynaklara bağlantılar sağlanmaktadır.  
  
 [SQL Server'da Sahiplik ve Kullanıcı Şeması Ayrımı](../../../../../docs/framework/data/adonet/sql/ownership-and-user-schema-separation-in-sql-server.md)  
 Nesne sahipliği ve kullanıcı-schema ayrımı açıklanmakta ve ek kaynaklara bağlantılar sağlanmaktadır.  
  
 [SQL Server’da Yetkilendirme ve İzinler](../../../../../docs/framework/data/adonet/sql/authorization-and-permissions-in-sql-server.md)  
 En az ayrıcalık ilkesini kullanarak izinleri verme açıklanmakta ve ek kaynaklara bağlantılar sağlanmaktadır.  
  
 [SQL Server’da Veri Şifreleme](../../../../../docs/framework/data/adonet/sql/data-encryption-in-sql-server.md)  
 SQL Server veri şifreleme seçenekleri açıklar ve ek kaynaklara bağlantılar sağlanmaktadır.  
  
 [SQL Server’da CLR Tümleştirme Güvenliği](../../../../../docs/framework/data/adonet/sql/clr-integration-security-in-sql-server.md)  
 CLR tümleştirme güvenlik kaynaklara bağlantılar sağlanmaktadır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliği](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
