---
title: SQL Server'da kimliğe bürünme izinleri özelleştirme
ms.date: 03/30/2017
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
ms.openlocfilehash: 182eadecbd5330f06fc1cd45d2c768b570f12bf5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596975"
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>SQL Server'da kimliğe bürünme izinleri özelleştirme
Çoğu uygulama, temel tablolar için erişimi kısıtlamak için sahiplik zinciri bağlı olan verilere erişmek için saklı yordamlar kullanır. Saklı yordamları ÇALIŞTIRMA izinlerini iptal etme veya temel tablolardan izinleri reddetme verebilirsiniz. SQL Server tabloları ve saklı yordam sahibi aynıysa çağıranın izinlerini kontrol yapmaz. Ancak, sahiplik zinciri nesneleri farklı sahipleri varsa veya dinamik SQL söz konusu olduğunda çalışmaz.  
  
 Kullanabileceğiniz EXECUTE AS yan tümcesinde başvurulan veritabanı nesneleri üzerinde çağıran izinlere sahip olmadığında bir saklı yordam. Geçerli yürütme bağlamı için Ara sunucu kullanıcı anahtarlanır EXECUTE AS yan tümcesi ise. İç içe geçmiş saklı yordamları ve tetikleyicileri, çağrıları yanı sıra, tüm kod proxy kullanıcının güvenlik bağlamı altında çalışır. Yürütme bağlamı yalnızca yürütme yordamın veya geri DÖNDÜRME deyimi verildiğinde sonra özgün çağırana döndürülür.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Bağlam değiştirme EXECUTE AS deyimi  
 Transact-SQL EXECUTE AS deyimi başka bir oturum açma veya veritabanı kullanıcının kimliğine bürünerek bir deyimi yürütme bağlamı geçiş yapmanızı sağlar. Bu, sorgular ve yordamları başka bir kullanıcı olarak test etmek için yararlı bir tekniktir.  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Oturum açma veya kullanıcı kimliğine bürünüyorsunuz ve DOĞRULAMASINDAN izinleriniz olmalıdır. Bu izin için örtük `sysadmin` tüm veritabanları için ve `db_owner` oldukları veritabanı rolü üyeleri.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>İzinleri ile EXECUTE AS yan tümcesi  
 Kullanabileceğiniz EXECUTE AS yan tümcesinde bir saklı yordam, tetikleyici veya kullanıcı tanımlı işlev (hariç, satır içi tablo değerli işlevler) tanımı üstbilgisi. Bu kullanıcı adı veya anahtar sözcüğü EXECUTE AS belirtilen bağlamında yürütmek yordamı neden olan yan tümcesi. Yalnızca gerekli izinleri yordamı tarafından erişilen nesneler üzerinde verme bir oturum açma için eşlenmemiş veritabanında bir proxy kullanıcı oluşturabilir. Yan tümcesi izinlerine sahip olmanız gerekir olarak yürütme belirtilen proxy kullanıcı tüm nesneleri modülü tarafından erişilir.  
  
> [!NOTE]
>  TRUNCATE TABLE gibi bazı eylemleri verilebilen izinlere sahip değilsiniz. Bir yordam içinde deyim ekleme ve ALTER TABLE izni bir ara sunucu kullanıcı belirterek, tabloyu yordamı yalnızca yürütme izinlerine sahip arayanlara kesmek için izinleri genişletebilirsiniz.  
  
 EXECUTE yan tümcesi iç içe geçmiş yordamları ve Tetikleyicileri dahil olmak üzere bu yordamın süresince geçerli olduğundan belirtilen bağlam. Bağlam, yürütme veya geri DÖNDÜRME deyimi verilen çağırana döner.  
  
 Üç adımı kullanan EXECUTE AS yan tümcesinde bir yordam.  
  
1.  Bir oturum açmayla değil veritabanında bir ara sunucu kullanıcısı oluşturun. Bu gerekli değildir, ancak izinleri yönetirken yardımcı olur.  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1.  Proxy kullanıcı gerekli izinleri verin.  
  
2.  Ekleme EXECUTE AS yan tümcesi saklı yordam veya kullanıcı tanımlı işlev.  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
>  Denetim gerektiren uygulamalar, arayanın özgün güvenlik bağlamı korunmaz çünkü bozabilir. SESSION_USER'ı, kullanıcı veya USER_NAME, geçerli kullanıcının kimliğini döndüren yerleşik işlevler EXECUTE AS ile ilişkili kullanıcıyı döndürür yan tümcesi, özgün çağırana.  
  
### <a name="using-execute-as-with-revert"></a>EXECUTE AS geri döndürme işlemi ile kullanma  
 Özgün yürütme bağlamına geri dönmek için geri Transact-SQL deyimini kullanabilirsiniz.  
  
 İsteğe bağlı yan tümcesi ile geri tanımlama yok = @variableName, sağlar, anahtar yürütme bağlamı çağırana geri @variableName değişkeni geçerli bir değer içeriyor. Bu bağlantı havuzu kullanıldığı ortamlarda çağırana geri yürütme bağlamı geçiş yapmanızı sağlar. Çünkü değerini @variableName EXECUTE AS çağırana yalnızca bilinen çağıran deyim, garanti yürütme bağlamı uygulamayı çağırır ve son kullanıcı tarafından değiştirilemez. Bağlantı kapalı olduğunda bu havuza döndürülür. Bağlantı hakkında daha fazla bilgi için bkz, ADO.NET havuzu [SQL Server Connection Pooling (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Yürütme bağlamı belirtme  
 Bir kullanıcı belirtmeye ek olarak, EXECUTE AS aşağıdaki anahtar sözcükler birini kullanabilirsiniz.  
  
-   ÇAĞIRICI. ARAYAN yürütme, varsayılan değerdir; diğer bir seçenek belirtilirse, yordamı çağıran güvenlik bağlamında yürütür.  
  
-   SAHİBİ. SAHİBİ olarak yürütülen yordamı sahibi bağlamında yordamı yürütür. Yordam tarafından sahip olunan bir şema oluşturulursa `dbo` veya veritabanı sahibi, Kısıtlanmamış izinlere sahip yordamı çalıştırır.  
  
-   KENDİ KENDİNE. Kendi KENDİNE yürütme, saklı yordamı oluşturan güvenlik bağlamında yürütür. Bu belirtilen bir kullanıcı olarak yürütülen eşdeğerdir belirtilen kullanıcı oluşturulması veya değiştirilmesi yordamı kişi burada.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [SQL Server’da Secure Dynamic SQL Yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [SQL Server'da Saklı Yordam İmzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)
- [Saklı Yordamlarla Verileri Değiştirme](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
