---
title: SQL Server'da Saklı Yordam İzinlerini Yönetme
description: Saklı yordamları veya Kullanıcı tanımlı işlevleri kullanarak erişim uygulayarak verilerinize ve veritabanı nesneleriniz için erişimi nasıl kısıtlayacağınızı öğrenin.
ms.date: 03/30/2017
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
ms.openlocfilehash: 44f6a0c3ca6b913c8998c4e5ddb60eab2b64e71b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172729"
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>SQL Server'da Saklı Yordam İzinlerini Yönetme

Veritabanınızda birden çok savunma hattı oluşturmanın bir yöntemi, saklı yordamları veya Kullanıcı tanımlı işlevleri kullanarak tüm veri erişimini uygulamaktır. Tablolar gibi temeldeki nesneler için tüm izinleri iptal eder veya reddeder ve saklı yordamlarda yürütme izinleri verir. Bu, veri ve veritabanı nesneleriniz etrafında etkin bir güvenlik çevresi oluşturur.  
  
## <a name="stored-procedure-benefits"></a>Saklı yordam avantajları  

 Saklı yordamlar aşağıdaki avantajlara sahiptir:  
  
- Veri mantığı ve iş kuralları, kullanıcıların veri ve nesnelere yalnızca geliştiricilerin ve veritabanı yöneticilerinin tarafından istenen şekilde erişebilmeleri için kapsüllenebilir.  
  
- Tüm Kullanıcı girişlerini doğrulayan parametreli saklı yordamlar, SQL ekleme saldırılarını sağlamak için kullanılabilir. Dinamik SQL kullanıyorsanız, komutlarınızı parametreleştirilediğinizden ve parametre değerlerini hiçbir şekilde doğrudan bir sorgu dizesine eklemeyin.  
  
- Geçici sorgulara ve veri değişikliklerine izin verilmez. Bu, kullanıcıların kötü amaçlı veya istenmeden veri yok etmesini ya da sunucu veya ağ üzerindeki performansa zarar veren sorguları yürütmesini engeller.  
  
- Hatalar, doğrudan istemci uygulamalarına geçirilmeden yordam kodunda işlenebilir. Bu, bir yoklama saldırısında yardımcı olabilecek hata iletilerinin döndürülmesini önler. Hataları günlüğe kaydedin ve sunucuda işleyin.  
  
- Saklı yordamlar bir kez yazılabilir ve birçok uygulama tarafından erişilebilir.  
  
- İstemci uygulamaların, temel alınan veri yapıları hakkında herhangi bir şeyi bilmeleri gerekmez. Saklı yordam kodu, değişiklikler parametre listelerini veya döndürülen veri türlerini etkilemediği sürece istemci uygulamalarında değişiklik gerektirmeden değiştirilebilir.  
  
- Saklı yordamlar, birden çok işlemi tek bir yordam çağrısında birleştirerek ağ trafiğini azaltabilir.  
  
## <a name="stored-procedure-execution"></a>Saklı yordam yürütme  

 Saklı yordamlar, kullanıcıların veritabanına erişim sağlamak için sahiplik zincirinden yararlanır ve böylece kullanıcılar veritabanı nesnelerine erişim için açık izne sahip olmaları gerekmez. Bir sahiplik zinciri birbirlerine her ardışık olarak erişen nesneler aynı kullanıcıya ait olduğunda oluşur. Örneğin, saklı yordam diğer saklı yordamları çağırabilir veya saklı yordam birden fazla tabloya erişebilir. Yürütme zincirindeki tüm nesneler aynı sahibe sahip ise SQL Server, yalnızca arayan için yürütme iznini denetler, çağıranın diğer nesneler üzerindeki izinleri değildir. Bu nedenle, yalnızca saklı yordamlarda yürütme izinleri vermeniz gerekir; temel alınan tablolardaki tüm izinleri iptal edebilir veya reddedebilirsiniz.  
  
## <a name="best-practices"></a>En İyi Uygulamalar  

 Saklı yordamları yazmak, uygulamanızı yeterince güvenli hale getirmek için yeterli değildir. Ayrıca, aşağıdaki olası güvenlik boşluklarını de göz önünde bulundurmanız gerekir.  
  
- Verilere erişebilmek istediğiniz veritabanı rollerinin saklı yordamları üzerinde yürütme izinleri verin.  
  
- Rol dahil olmak üzere veritabanındaki tüm roller ve kullanıcılar için temel alınan tabloların tüm izinlerini iptal edin veya reddedin `public` . Tüm kullanıcılar izinleri herkese devralınır. Bu nedenle, izinleri reddetme, `public` yalnızca sahiplerin ve `sysadmin` üyelerin erişimi olduğu anlamına gelir; diğer tüm kullanıcılar diğer rollerdeki üyelikle izinleri almayacaktır.  
  
- Veya rollerine Kullanıcı veya rol eklemeyin `sysadmin` `db_owner` . Sistem yöneticileri ve veritabanı sahipleri, tüm veritabanı nesnelerine erişebilir.  
  
- Hesabı devre dışı bırakın `guest` . Bu, anonim kullanıcıların veritabanına bağlanmasını engeller. Yeni veritabanlarında Konuk hesabı varsayılan olarak devre dışıdır.  
  
- Hata işleme ve günlük hatalarını uygulayın.  
  
- Tüm Kullanıcı girişlerini doğrulayan parametreli saklı yordamlar oluşturun. Tüm Kullanıcı girişlerini güvenilir değil olarak değerlendirin.  
  
- Mutlak gerekmedikçe dinamik SQL kullanmaktan kaçının. Transact-SQL QUOTENAME () işlevini kullanarak bir dize değerini sınırlandırın ve giriş dizesindeki sınırlandırıcının herhangi bir oluşumunu kaçış.  
  
## <a name="external-resources"></a>Dış Kaynaklar  

 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Saklı yordamlar](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) ve [SQL ekleme](/sql/relational-databases/security/sql-injection)|Makaleler, saklı yordamların nasıl oluşturulduğunu ve SQL ekleme 'nin nasıl çalıştığını açıklamaktadır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../securing-ado-net-applications.md)
- [SQL Server Güvenliğine Genel Bakış](overview-of-sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](application-security-scenarios-in-sql-server.md)
- [SQL Server’da Secure Dynamic SQL Yazma](writing-secure-dynamic-sql-in-sql-server.md)
- [SQL Server'da Saklı Yordam İmzalama](signing-stored-procedures-in-sql-server.md)
- [SQL Server'da Kimliğe Bürünme İzinlerini Özelleştirme](customizing-permissions-with-impersonation-in-sql-server.md)
- [Saklı Yordamlarla Verileri Değiştirme](../modifying-data-with-stored-procedures.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
