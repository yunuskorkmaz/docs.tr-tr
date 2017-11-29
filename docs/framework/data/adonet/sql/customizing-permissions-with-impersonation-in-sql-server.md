---
title: "Kimliğe bürünme SQL Server'daki izinlerle özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc733d09-1d6d-4af0-9c4b-8d24504860f1
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cde4fafaa10d7c9b495d4f98ddcd42c7f8a7524a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="customizing-permissions-with-impersonation-in-sql-server"></a>Kimliğe bürünme SQL Server'daki izinlerle özelleştirme
Birçok uygulama, sahipliği tablolar temel erişimi kısıtlamak için zincirleme bağlı olan verilere erişmek için saklı yordamları kullanın. Saklı yordamlar, yürütme izinlerini iptal etme veya reddetme temel tablolar üzerindeki izinleri verebilirsiniz. Tabloları ve saklı yordam aynı sahip varsa, SQL Server çağıran izinleri denetlemez. Ancak, sahipliği zincirleme nesneleri farklı sahipleri varsa veya dinamik SQL söz konusu olduğunda işe yaramaz.  
  
 Kullanabileceğiniz EXECUTE AS yan tümcesinde başvurulan veritabanı nesneleri üzerinde çağıran izinlere sahip olmadığında bir saklı yordam. Etkisi EXECUTE AS yan tümcesi yürütme bağlamı proxy kullanıcıya anahtarlanır olduğu. İç içe geçmiş saklı yordamları ve tetikleyicileri, yapılan her çağrı yanı sıra tüm kod proxy kullanıcı güvenlik bağlamı altında çalışır. Yürütme bağlamı özgün çağırana yalnızca yürütme yordamın veya REVERT deyimi verildiğinde sonra geri döndürüldü.  
  
## <a name="context-switching-with-the-execute-as-statement"></a>Bağlam EXECUTE AS değiştirme deyimi  
 Transact-SQL EXECUTE AS deyimi bir deyimi yürütme bağlamı başka bir oturum açma veya veritabanı kullanıcı kimliğine bürünerek geçiş yapmanızı sağlar. Bu, sorgular ve yordamları başka bir kullanıcı olarak test etmek için kullanışlı bir tekniktir.  
  
```  
EXECUTE AS LOGIN = 'loginName';  
EXECUTE AS USER = 'userName';  
```  
  
 Oturum açma veya kullanıcı kimliğine bürünme özelliklerini al izinleri olması gerekir. Bu izin için örtük `sysadmin` tüm veritabanları için ve `db_owner` oldukları veritabanlarında Rol üyeleri.  
  
## <a name="granting-permissions-with-the-execute-as-clause"></a>EXECUTE AS izinlerle verme yan tümcesi  
 Kullanabileceğiniz EXECUTE AS yan tümcesinde bir saklı yordam, tetikleyici veya kullanıcı tanımlı işlev (dışında satır içi tablo değerli işlevler) tanımı üstbilgisi. Bu kullanıcı adı ya da anahtar sözcük EXECUTE AS belirtilen bağlamında yürütmek için yordamı neden yan tümcesi. Yalnızca gerekli izinleri yordamı tarafından erişilen nesneler üzerinde verme bir oturum açma eşlenmemiş veritabanında bir proxy kullanıcısı oluşturabilirsiniz. EXECUTE yan tümcesi modül tarafından erişilen tüm nesneler üzerinde izinleri olmalıdır olarak belirtilen yalnızca proxy kullanıcı.  
  
> [!NOTE]
>  TRUNCATE TABLE gibi bazı eylemleri verilebilen izinlere sahip değil. Bir yordam içindeki deyim ekleme ve ALTER TABLE izinlere sahip bir proxy kullanıcı belirterek yordamı yalnızca yürütme izinlerine sahip arayanlar tabloya kesmek için izinleri genişletebilirsiniz.  
  
 EXECUTE yan tümcesi iç içe geçmiş yordamları ve Tetikleyicileri dahil olmak üzere bu yordam boyunca geçerli olarak belirtilen bağlamı. Bağlam çağırana yürütme veya geri DÖNDÜRME deyimi verilen olduğunda döner.  
  
 EXECUTE AS kullanarak söz konusu üç adım vardır yan tümcesinde bir yordam.  
  
1.  Proxy kullanıcı bir oturum eşlenmemiş veritabanı oluşturun. Bu gerekli değildir, ancak izinleri yönetirken yardımcı olur.  
  
```  
CREATE USER proxyUser WITHOUT LOGIN  
```  
  
1.  Proxy kullanıcı gerekli izinleri verin.  
  
2.  Ekleme EXECUTE AS yan tümcesi saklı yordam veya kullanıcı tanımlı işlev.  
  
```  
CREATE PROCEDURE [procName] WITH EXECUTE AS 'proxyUser' AS ...  
```  
  
> [!NOTE]
>  Arayanın özgün güvenlik bağlamı korunmayan çünkü denetim gerektiren uygulamalar bozulabilir. Örneğin SESSION_USER'ı, kullanıcı veya USER_NAME, geçerli kullanıcının kimliğini döndürür yerleşik işlevler EXECUTE AS ile ilişkili kullanıcıyı döndürür yan tümcesi, özgün çağıran.  
  
### <a name="using-execute-as-with-revert"></a>EXECUTE AS REVERT ile kullanma  
 Özgün yürütme bağlamı geri dönmek için geri Transact-SQL deyimini kullanabilirsiniz.  
  
 İsteğe bağlı yan tümcesi ile Hayır geri tanımlama bilgisi = @variableName, geçiş yürütme bağlamı geri çağırana varsa verir @variableName değişkeni doğru değeri içerir. Bu bağlantı havuzu kullanıldığı ortamlarda çağırana geri yürütme bağlamı geçiş yapmanızı sağlar. Çünkü değerini @variableName yalnızca EXECUTE AS çağırana bilinen deyimi, çağıran ise yürütme bağlamı uygulamayı çağıran son kullanıcı tarafından değiştirilemez. Bağlantı kapalı olduğunda havuza geri döner. ADO.NET, havuzu bağlantısı hakkında daha fazla bilgi için bkz [SQL Server bağlantı havuzu (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
### <a name="specifying-the-execution-context"></a>Yürütme bağlamı belirtme  
 Bir kullanıcı belirtmeye ek olarak da EXECUTE AS herhangi şu anahtar sözcüklerden biri ile kullanabilirsiniz.  
  
-   ÇAĞIRICI. ARAYAN yürütülen varsayılandır; diğer bir seçenek belirtilmişse, yordamı çağıran güvenlik bağlamında yürütür.  
  
-   SAHİBİ. SAHİBİ olarak yürütülen yordamı yordamı sahibi bağlamında yürütür. Yordam tarafından sahip olunan bir şemadaki oluşturduysanız `dbo` veya veritabanı sahibi Kısıtlanmamış izinlerle yordamı çalıştırır.  
  
-   KENDİ KENDİNİ. KENDİNİ yürütülen Oluşturucusu saklı yordamı, güvenlik bağlamını yürütür. Bu belirtilen bir kullanıcı olarak yürütülen eşdeğerdir belirtilen kullanıcı oluşturma veya değiştirme yordamı kişi olduğu.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynaklara bakın.  
  
|Kaynak|Açıklama|  
|--------------|-----------------|  
|[İçerik Geçişi](http://msdn.microsoft.com/library/ms188268.aspx) SQL Server Çevrimiçi Kitapları'nda|EXECUTE AS kullanmayı açıklayan konulara bağlantılar içerir yan tümcesi.|  
|[Özel izin kümeleri oluşturmak için EXECUTE AS kullanarak](http://msdn.microsoft.com/library/ms190384.aspx) ve [modülleri EXECUTE AS kullanarak](http://msdn.microsoft.com/library/ms178106.aspx) SQL Server Çevrimiçi Kitapları'nda|Konular, EXECUTE AS kullanmayı açıklar yan tümcesi.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ADO.NET uygulamalarının güvenliğini sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server güvenlik genel bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'daki uygulama güvenlik senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [Saklı yordamlar SQL Server'daki izinlerle yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [SQL Server'da güvenli dinamik SQL yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [Saklı yordamlar SQL Server'daki imzalama](../../../../../docs/framework/data/adonet/sql/signing-stored-procedures-in-sql-server.md)  
 [Saklı yordamlar verilerle değiştirme](../../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
