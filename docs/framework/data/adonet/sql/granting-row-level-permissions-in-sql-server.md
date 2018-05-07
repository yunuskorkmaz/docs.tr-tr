---
title: SQL Server'da satır düzeyi izinleri verme
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 5f777b47c9b2f92c40fec01b4ff0c35fc28dbd89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="granting-row-level-permissions-in-sql-server"></a>SQL Server'da satır düzeyi izinleri verme
Bazı senaryolarda, hangi yalnızca verme, iptal etme veya reddetme izinleri sağlayan daha daha ayrıntılı bir düzeyde veri erişimi denetlemek için bir gereksinim yoktur. Örneğin, hastaneler veritabanı uygulaması yalnızca kendi hastalar ilgili bilgilerine erişmek için kısıtlı olacak şekilde tek tek Doktorlar gerektirebilir. Benzer gereksinim Finans, yasalar, kamu ve Askeri uygulamalar dahil olmak üzere birçok ortamlarda yoktur. Bu senaryoyu ele yardımcı olmak için SQL Server 2016 sağlayan bir [satır düzeyi güvenlik](https://msdn.microsoft.com/library/dn765131.aspx) basitleştirir ve güvenlik ilkesinde satır düzeyi erişim mantığı merkezi hale getirir özelliği. SQL Server'ın önceki sürümleri için benzer işlevselliği satır düzeyi filtreleme yürürlüğe için görünümleri kullanarak elde edilebilir.  
  
## <a name="implementing-row-level-filtering"></a>Satır düzeyi filtre uygulama  
 Satır düzeyi filtreleme uygulamalar gibi tek bir tabloda yukarıdaki Hastanenin örnekte bilgilerini depolamak için kullanılır. Satır düzeyi her satır filtresi uygulamak için bir kullanıcı adı, etiket veya başka bir tanımlayıcı gibi farklılaştırıcı bir parametreyi tanımlayan bir sütun vardır. Bir güvenlik ilkesi veya kullanıcının erişebildiği satırları filtreler tabloda bir görünüm oluşturun. Kullanıcı çalıştırabileceğiniz sorgu türlerini denetlemek için parametreli saklı yordamlar, oluşturursunuz.  
  
 Aşağıdaki örnekte, bir kullanıcı veya oturum açma adını temel alarak satır düzeyi filtrelemenin nasıl yapılandırılacağı açıklanmaktadır:  
  
-   Adı depolamak için bir sütun ekleme tablo oluşturun.  
  
-   Satır düzeyi filtreleme etkinleştirin:  
  
    -   SQL Server 2016 veya sonraki bir sürümü kullanıyorsanız veya [Azure SQL veritabanı](https://docs.microsoft.com/azure/sql-database/), satırları kısıtlama tablosunda bir koşul döndürülen ya da eşleşen olanlar (CURRENT_USER() kullanarak geçerli veritabanı kullanıcısı ekler bir güvenlik ilkesi oluşturma Yerleşik işlevi) veya (SUSER_SNAME() yerleşik işlevi kullanılarak) geçerli oturum açma adı:  
  
        ```tsql  
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
  
    -   2016 önce SQL Server'ın bir sürümünü kullanıyorsanız, bir görünümü kullanarak benzer işlevselliği elde edebilirsiniz:  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   Seçin, Ekle, Güncelleştir ve verileri silmek için saklı yordamlar oluşturun. Saklı yordamlar filtreleme bir güvenlik ilkesi tarafından geçirilmeden, temel tablo bu işlemleri doğrudan gerçekleştirmeniz gerekir; Aksi takdirde, filtreleme görünüm tarafından geçirilmeden, saklı yordamları yerine karşı görünüm çalışacağı. Güvenlik İlkesi veya Görünüm döndürülen veya kullanıcı sorgular tarafından değiştirilen satırları otomatik olarak filtre uygular ve saklı yordam doğrudan sorgu erişimi olan kullanıcılar çıkarımını sorguları başarılı bir şekilde çalışmasını engellemek için daha zor bir güvenlik sınırı sağlar filtrelenmiş veri varlığını.  
  
-   Saklı yordamlar için veri eklemek, yakalama güvenlik ilkesi veya görünümde belirtilen aynı işlevini kullanarak kullanıcı adı ve bu değer kullanıcı adı sütuna ekleyin.  
  
-   Tabloları (ve görünümler, eğer varsa) tüm izinleri reddetmek için `public` rol. Kullanıcılar, filtre koşulu kullanıcı veya rol değil, oturum açma adları bağlı olduğu diğer veritabanı rollerden devralmak mümkün olmayacaktır.  
  
-   Veritabanı rolleri için saklı yordamları hakkında GRANT YÜRÜTÜN. Kullanıcıların sağlanan saklı yordamları yalnızca verilere erişebilir.  
  
## <a name="external-resources"></a>Dış Kaynaklar  
 Daha fazla bilgi için aşağıdaki kaynağa bakın.  
  
|||  
|-|-|  
|[Satır ve hücre düzeyi güvenlik sınıflandırılmış veritabanları kullanarak SQL Server 2005'te uygulama](http://go.microsoft.com/fwlink/?LinkId=98227) üzerinde SQL Server TechCenter sitesi.|Satır ve hücre düzeyi güvenlik sınıflandırılmış veritabanı güvenlik gereksinimlerini karşılamak için nasıl kullanılacağını açıklar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Satır düzeyi güvenlik](https://msdn.microsoft.com/library/dn765131.aspx)  
 [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)  
 [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)  
 [SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)  
 [SQL Server’da Secure Dynamic SQL Yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
