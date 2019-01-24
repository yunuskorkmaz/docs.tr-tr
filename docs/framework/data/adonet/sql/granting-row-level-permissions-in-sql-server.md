---
title: SQL Server'da satır düzeyinde izinler verme
ms.date: 03/30/2017
ms.assetid: a55aaa12-34ab-41cd-9dec-fd255b29258c
ms.openlocfilehash: 28e552e005cdfa0b4c69ff95927b938fa3898193
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553783"
---
# <a name="granting-row-level-permissions-in-sql-server"></a>SQL Server'da satır düzeyinde izinler verme
Bazı senaryolarda, hangi yalnızca verme, iptal etme veya reddetme izinleri sağlar. daha fazla ayrıntılı bir düzeyde verilere erişimi denetlemek için bir gereksinim yoktur. Örneğin, bir hastane veritabanı uygulaması tek Doktorlar hastaların için yalnızca ilgili bilgiler erişimle sınırlı olmasını gerektirebilir. Benzer gereksinimleri, Finans, yasa, resmi ve Askeri uygulamalar dahil, birçok ortamlarında mevcut. Bu senaryolara yardımcı olmak için SQL Server 2016 sağlar. bir [satır düzeyi güvenlik](https://msdn.microsoft.com/library/dn765131.aspx) basitleştirir ve satır düzeyinde erişim mantığı güvenlik ilkesinde otomatik özelliği. Satır düzeyinde filtreleme geçireceğini görünümlerini kullanarak SQL Server'ın önceki sürümleri için benzer bir işlevsellik gerçekleştirilebilir.  
  
## <a name="implementing-row-level-filtering"></a>Satır düzeyi filtre uygulama  
 Satır düzeyinde filtreleme uygulamaları gibi tek bir tabloda yukarıdaki hastane örnekte bilgilerini depolamak için kullanılır. Satır düzeyi her bir satır filtresi uygulamak için bir kullanıcı adı, etiket veya başka bir tanımlayıcı gibi ayırt edici bir parametre tanımlayan bir sütun vardır. Bir güvenlik ilkesini veya kullanıcının erişebildiği satırları filtreler tablosunda bir görünüm oluşturun. Daha sonra kullanıcı yürütebilir sorguları türlerini denetlemek için parametreli saklı yordamlar, oluşturursunuz.  
  
 Aşağıdaki örnek, satır düzeyinde bir kullanıcı veya oturum açma adına göre filtrelemeyi yapılandırma açıklar:  
  
-   Adı depolamak için bir sütun ekleme, tablo oluşturun.  
  
-   Satır düzeyinde filtreleme etkinleştir:  
  
    -   SQL Server 2016 veya sonraki bir sürümünü kullanıyorsanız veya [Azure SQL veritabanı](https://docs.microsoft.com/azure/sql-database/), satırları kısıtlama tablosunda bir koşul döndürülen ya da eşleşen olanlar (CURRENT_USER() kullanarak geçerli bir veritabanı kullanıcısı ekleyen bir güvenlik ilkesi oluşturma Yerleşik işlev) veya (SUSER_SNAME() yerleşik işlevi kullanılarak), geçerli oturum açma adı:  
  
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
  
    -   SQL Server 2016'dan önce bir sürümü kullanıyorsanız benzer işlevselliği bir görüntü kullanarak elde edebilirsiniz:  
  
        ```tsql  
        CREATE VIEW vw_MyTable  
        AS  
            RETURN SELECT * FROM MyTable  
            WHERE UserName = SUSER_SNAME()  
        GO  
        ```  
  
-   Seçin, ekleme, güncelleştirme ve verileri silmek için saklı yordamlar oluşturun. Güvenlik İlkesi tarafından filtreleme geçirilmeden, saklı yordamları doğrudan temel tablo bu işlemleri gerçekleştirmeniz gerekir; Aksi takdirde, filtre tarafından bir görünümü geçirilmeden, saklı yordamları yerine karşı görünümü çalışması. Güvenlik İlkesi veya Görünüm otomatik olarak döndürülen veya kullanıcı sorgular tarafından değiştirilen satırları filtreleyen ve saklı yordam doğrudan sorgu erişimi olan kullanıcılar başarıyla çıkarımını sorgular çalıştırılmasını engellemek için daha zor bir güvenlik sınırı sağlar filtrelenmiş veri varlığını.  
  
-   Veri ekleme, saklı yordamlar, yakalama aynı güvenlik ilkesi veya görünümü'nde belirtilen işlevi kullanarak kullanıcı adı ve değeri kullanıcıadı sütuna ekleyin.  
  
-   Tüm tablolar (ve görünümler, eğer varsa) izinlerini reddetmek için `public` rol. Kullanıcılar, filtre koşulu kullanıcı veya rol değil, oturum açma adları bağlı olduğu diğer veritabanı rollerden devralmak mümkün olmayacaktır.  
  
-   GRANT veritabanı rollerine saklı yordamlar YÜRÜTÜN. Kullanıcılar sağlanan saklı yordamları yalnızca verilere erişebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Satır düzeyi güvenlik](https://msdn.microsoft.com/library/dn765131.aspx)
- [ADO.NET Uygulamalarının Güvenliğini Sağlama](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [SQL Server Güvenliğine Genel Bakış](../../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)
- [SQL Server'da Uygulama Güvenliği Senaryoları](../../../../../docs/framework/data/adonet/sql/application-security-scenarios-in-sql-server.md)
- [SQL Server'da Saklı Yordam İzinlerini Yönetme](../../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)
- [SQL Server’da Secure Dynamic SQL Yazma](../../../../../docs/framework/data/adonet/sql/writing-secure-dynamic-sql-in-sql-server.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
