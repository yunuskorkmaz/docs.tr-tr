---
title: "Saklı yordamlar SQL Server'daki izinlerle yönetme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 08fa34e8-2ffa-470d-ba62-e511a5f8558e
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 806cd23060dde3f7b466df0d4ce39162353380e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="managing-permissions-with-stored-procedures-in-sql-server"></a>Saklı yordamlar SQL Server'daki izinlerle yönetme
Veritabanınızı geçici savunma çok satırlı oluşturma yöntemi, saklı yordam veya kullanıcı tanımlı işlevler kullanarak tüm veri erişim uygulamaktır. Tablolar gibi temel nesneler için tüm izinleri reddetme iptal etme ve saklı yordamlar Yürütme izinleri. Bu etkin bir güvenlik çevre geçici verileri ve veritabanı nesnelerini oluşturur.  
  
## <a name="stored-procedure-benefits"></a>Saklı yordam avantajları  
 Saklı yordamlar aşağıdaki avantajlara sahiptir:  
  
-   Kullanıcıların veri ve nesneleri geliştiricilerinin ve veritabanı yöneticilerinin amaçladığınız şekilde erişebilmesi için veri mantığı ve iş kuralları kapsüllenmiş.  
  
-   Tüm kullanıcı girişi doğrulama parametreli saklı yordamlar SQL ekleme saldırıları engel olmak için kullanılabilir. Dinamik SQL kullanırsanız, komutlarınızı Parametreleştirme emin olun ve hiçbir zaman doğrudan bir sorgu dizesi parametre değerlerini içerir.  
  
-   Geçici sorgular ve veri değişiklikleri izin verilmeyen. Bu, kullanıcıların kötü amaçlı olarak veya yanlışlıkla veri yok etme veya sunucu veya ağ performansına bozacak sorguları yürütme engeller.  
  
-   Hataları doğrudan istemci uygulamaları için geçirilen olmadan yordamı kodda işlenebilir. Bu, hata iletileri yoklama saldırısında yardımcı döndürülmesini engeller. Hataları günlüğe kaydetmek ve sunucu üzerinde tanıtıcı.  
  
-   Saklı yordamlar kez yazılmış ve birçok uygulamalar tarafından erişilen.  
  
-   İstemci uygulamaları temel alınan veri yapılarını hakkında hiçbir şey bilmeniz gerek yoktur. Saklı yordam kod değişiklikleri parametre listeleri etkilemez sürece istemci uygulamalarında değişiklik gerek kalmadan değiştirilemez veya veri türleri döndürüldü.  
  
-   Saklı yordamlar, bir yordam çağrısı birden çok işleme birleştirerek ağ trafiğini azaltabilir.  
  
## <a name="stored-procedure-execution"></a>Saklı yordam yürütme  
 Böylece kullanıcılar, açık veritabanı nesnelerini erişim iznine sahip gerekmez. veri erişim sağlamak için zincirleme sahipliği yordamları yararlanma depolanır. Birbirine sırayla erişim nesneler aynı kullanıcı tarafından sahip olunan bir sahiplik zinciri bulunmaktadır. Örneğin, bir saklı yordam diğer saklı yordamları çağırabilir veya saklı yordam birden çok tablo erişebilir. Yürütme zincirindeki tüm nesnelerin aynı sahip sonra SQL Server, çağıran EXECUTE izni yalnızca denetler olmayan diğer nesneleri arayanın izinleri. Bu nedenle yalnızca saklı yordam Yürütme izinleri vermeniz gerekir; iptal etmek veya arka plandaki tablolar üzerindeki tüm izinleri reddetme.  
  
## <a name="best-practices"></a>En İyi Yöntemler  
 Saklı yordamlar yalnızca yazma yeterli uygulamanızın güvenliğini sağlamak için yeterli değildir. Ayrıca, aşağıdaki olası güvenlik açıklarını düşünmeniz gerekir.  
  
-   Saklı yordamlar verilerine erişebilir olmasını istediğiniz veritabanı rolleri için yürütme izinlerini verin.  
  
-   İptal etmek veya tüm rolleri ve kullanıcılar veritabanında temel alınan tablolara tüm izinleri reddetme dahil olmak üzere `public` rol. Tüm kullanıcıların izinleri gelen ortak devralır. Bu nedenle izinleri reddetme `public` anlamına gelir, yalnızca sahipleri ve `sysadmin` üyeleri erişimi vardır; diğer tüm kullanıcıların diğer rollerdeki üyeliğinin devralmak mümkün olmayacaktır.  
  
-   Kullanıcıları veya rolleriyle eklemeyin `sysadmin` veya `db_owner` rolleri. Sistem yöneticileri ve veritabanı sahipleri tüm veritabanı nesnelerini erişebilir.  
  
-   Devre dışı `guest` hesabı. Bu, anonim kullanıcılar veritabanına bağlanırken engeller. Konuk hesabını yeni veritabanları varsayılan olarak devre dışıdır.  
  
-   Hata işleme ve günlük hatalar uygulayın.  
  
-   Tüm kullanıcı girişi doğrulama parametreli saklı yordamlar oluşturun. Tüm kullanıcı girişi olarak güvenilmeyen kabul eder.  
  
-   Dinamik SQL sürece kaçının kesinlikle gerekli. Bir dize değeri sınırlandırmak ve giriş dizisinde sınırlayıcısı olayı kaçınmak için Transact-SQL QUOTENAME() işlevini kullanın.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[Saklı yordamlar](http://msdn.microsoft.com/library/ms190782.aspx) ve [SQL ekleme](http://go.microsoft.com/fwlink/?LinkId=98234) SQL Server Çevrimiçi Kitapları'nda|Konularda saklı yordamlar oluşturma ve SQL ekleme nasıl çalıştığı açıklanmaktadır.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server güvenlik genel bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'daki uygulama güvenlik senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server'da güvenli dinamik SQL yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Saklı yordamlar SQL Server'daki imzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Kimliğe bürünme SQL Server'daki izinlerle özelleştirme](../../../../../docs/framework/data/adonet/sql/customizing-permissions-with-impersonation-in-sql-server.md)  
 [Saklı yordamlar verilerle değiştirme](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
