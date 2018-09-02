---
title: SQL Server'da saklı yordam izinlerini yönetme
ms.date: 03/30/2017
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
ms.openlocfilehash: e6161195682964ac9063cbee65d26ade601ef66c
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425204"
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>SQL Server'da saklı yordam izinlerini yönetme
Bir yöntem çok satırlı defense veritabanınızı geçici olarak oluşturma, saklı yordamları ve kullanıcı tanımlı işlevleri kullanarak tüm veri erişim uygulamaktır. Tablolar gibi temel nesneler için tüm izinleri reddetme ve saklı yordamları yürütme izinlerini iptal etme. Bu, geçici verileri ve veritabanı nesnelerinizi bir güvenlik çevresi etkili bir şekilde oluşturur.  
  
## <a name="stored-procedure-benefits"></a>Saklı yordam avantajları  
 Saklı yordamlar aşağıdaki avantajlara sahiptir:  
  
-   Kullanıcı verileri ve nesneleri geliştiricileri ve Veritabanı yöneticileri amaçladığınız şekilde erişebilmesi için veri mantığını ve iş kuralları kapsüllenmiş.  
  
-   Tüm kullanıcı girişini doğrulama parametreli saklı yordamları, SQL ekleme saldırılarına karşı korunmanıza kullanılabilir. Dinamik SQL kullanırsanız, Komutlarınızın Parametreleştirme emin olun ve hiçbir zaman doğrudan bir sorgu dizesi parametresi değerleri içerir.  
  
-   Geçici sorgular ve veri değişiklikleri izin verilmiyor. Bu, kullanıcıların kötü amaçlı olarak veya yanlışlıkla veri yok etme veya sunucu veya ağ performansı bozacak sorgular yürütme engeller.  
  
-   Yordam kodunda hataları doğrudan istemci uygulamaları için geçirilen olmadan işlenebilir. Bu, hata iletileri algılama saldırısında yardımcı döndürülmesini önler. Hataları günlüğe kaydetmek ve bunları sunucuda işlemesi.  
  
-   Saklı yordamlar kez yazılmış ve birçok uygulama tarafından erişilebilir.  
  
-   İstemci uygulamaları, temel alınan veri yapıları hakkında bir şey bilmek gerekmez. Saklı yordam kodu değişiklikleri parametre listeleri etkilemez sürece, istemci uygulamalarında bir değişikliğe gerek kalmadan değiştirilebilir ya da veri türleri döndürdü.  
  
-   Saklı yordamlar, bir yordam çağrısı birden fazla işlemi birleştirerek ağ trafiğini azaltabilir.  
  
## <a name="stored-procedure-execution"></a>Saklı yordam yürütme  
 Yordamları faydalanın-kullanıcılar, veritabanı nesneleri erişmek için açık izniniz gerekmez. böylece veri erişim sağlamak için zincirleme sahipliği depolanır. Birbirine sıralı olarak erişen nesneler aynı kullanıcı tarafından sahip olunan bir sahiplik zinciri bulunmaktadır. Örneğin, diğer saklı yordamlara bir saklı yordam çağırabilir veya bir saklı yordam birden çok tablo erişebilirsiniz. Yürütme zincirindeki tüm nesnelerin aynı bir sahip ve ardından SQL Server yalnızca arayan için yürütme izni denetler, arayanın izinlerin diğer nesneler üzerinde değil. Bu nedenle saklı yordamlar yalnızca yürütme izinleri vermeniz gerekir; iptal etmek ya da temel alınan tablolar üzerindeki tüm izinleri reddetme.  
  
## <a name="best-practices"></a>En İyi Yöntemler  
 Saklı yordamlar yalnızca yazma yeterince uygulamanızın güvenliğini sağlamak için yeterli değildir. Ayrıca, aşağıdaki olası güvenlik açıkları düşünmeniz gerekir.  
  
-   Veritabanı rolleri verilerine erişebilir olmasını istediğiniz için saklı yordamları ÇALIŞTIRMA izinlerini verin.  
  
-   İptal etmek ya da temel alınan tablolar için tüm roller ve kullanıcılar veritabanındaki tüm izinleri reddetme dahil olmak üzere `public` rol. Tüm kullanıcılar, gelen genel izinleri devralır. Bu nedenle izinleri reddetme `public` anlamına gelir, yalnızca sahipleri ve `sysadmin` üye erişimi vardır; diğer tüm kullanıcıların izinleri, diğer rol üyelikleri devralınacak mümkün olmayacaktır.  
  
-   Kullanıcıların rollerini veya eklemeyin `sysadmin` veya `db_owner` rolleri. Sistem yöneticileri ve veritabanı sahipleri, tüm veritabanı nesnelere erişebilir.  
  
-   Devre dışı `guest` hesabı. Bu, anonim kullanıcıların veritabanına bağlanmasını engeller. Konuk hesabı yeni veritabanları varsayılan olarak devre dışıdır.  
  
-   Hata işleme ve günlük hatalar uygulayın.  
  
-   Tüm kullanıcı girişini doğrulama parametreli saklı yordamlar oluşturun. Tüm kullanıcı girişi, güvenilmeyen olarak kabul eder.  
  
-   Dinamik SQL yapmaktan kaçının kesinlikle gerekli. Bir dize değeri sınırlandırmak ve sınırlayıcı giriş dizesindeki tüm oluşumlarıyla kaçış için Transact-SQL QUOTENAME() işlevini kullanın.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Saklı yordamları](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) ve [SQL ekleme](https://go.microsoft.com/fwlink/?LinkId=98234) SQL Server Çevrimiçi Kitapları'nda|Konular, saklı yordamlar oluşturma ve SQL ekleme nasıl çalıştığını açıklar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server’da Secure Dynamic SQL Yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [SQL Server'da Saklı Yordam İmzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Saklı Yordamlarla Verileri Değiştirme](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
