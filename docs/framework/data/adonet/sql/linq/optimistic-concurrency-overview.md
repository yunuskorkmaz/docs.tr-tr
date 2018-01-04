---
title: "İyimser eşzamanlılık: genel bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 91684f1971692e83664fe41a0385a6d68b327237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="optimistic-concurrency-overview"></a>İyimser eşzamanlılık: genel bakış
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]İyimser eşzamanlılık denetimini destekler. Aşağıdaki tabloda iyimser eşzamanlılık uygulamak terimler açıklanmıştır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] belgeleri:  
  
|Koşulları|Açıklama|  
|-----------|-----------------|  
|eşzamanlılık|Durum aynı anda iki veya daha fazla kullanıcı veritabanı satıra güncelleştirmeyi deneyin.|  
|Eşzamanlılık çakışması|İki veya daha fazla kullanıcı aynı anda bir veya daha fazla sütun satır için çakışan değerleri gönderme deneyin durum.|  
|eşzamanlılık denetimi|Eşzamanlılık çakışmalarını çözmek için kullanılan yöntem.|  
|İyimser eşzamanlılık denetimi|İlk gönderilecek değişiklikleri sorgulamasına önce diğer işlemleri bir satır değerleri değişip değişmediğini araştırır yöntemi.<br /><br /> İle karşılaştırın *eşzamanlılık denetim*, eşzamanlılık çakışmaları önlemek için kayıt kilitler.<br /><br /> *İyimser* denetim bir işlem başka bir işlemle tahmin edilemez olmalıdır engellemesini olasılığını algıladığından bu nedenle ifade.|  
|çakışma çözümü|Veritabanını yeniden sorgulama ve farkları mutabık kılma çakışan öğe yenileme işlemi.<br /><br /> Bir nesne yenilendiğinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişikliği İzleyicisi aşağıdaki veriler tutar:<br /><br /> -İlk olarak veritabanından alınır ve güncelleştirme için kullanılan değerlerini denetleyin.<br />-Yeni veritabanı değerlerini kullanarak sonraki sorgu.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ardından nesne (diğer bir deyişle, bir veya daha fazla üye değerlerinin değiştirilip) çakışma olup olmadığını belirler. Nesne, çakışma ise [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sonraki çakışma üyeleri olan belirler.<br /><br /> Herhangi bir üyenin çakışma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bulur çakışma listesine eklenir.|  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli, bir *iyimser eşzamanlılık çakışması* aşağıdaki koşulların her ikisi de doğruysa oluşur:  
  
-   Değişiklikler veritabanına göndermek istemci dener.  
  
-   İstemcinin son okuyabilir bu yana veritabanında bir veya daha fazla güncelleştirme denetimi değerleri güncelleştirildi.  
  
 Bu çakışma çözümlemesi nesne hangi üyelerinin çakışıyor bulmak ve bununla ilgili istediğiniz karar içerir.  
  
> [!NOTE]
>  Yalnızca üyeleri eşlenen olarak <xref:System.Data.Linq.Mapping.UpdateCheck.Always> veya <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> iyimser eşzamanlılık denetimlerinde katılın. Denetimsiz işaretlenmiş üyeleri için gerçekleştirilen <xref:System.Data.Linq.Mapping.UpdateCheck.Never>. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Örnek  
 Örneğin, aşağıdaki senaryoda, bir satır için veritabanı sorgulayarak bir güncelleştirme hazırlamak Kullanıcı1 başlatır. Kullanıcı1 Alfreds, Maria ve satış değerlerle satırını alır.  
  
 Kullanıcı1 Alfred ve pazarlama departmanı sütuna değerini Yöneticisi sütunun değeri değiştirmek istiyor. Bu değişiklikleri Kullanıcı1 göndermeden önce kullanıcı2 değişiklikler veritabanına gönderdi. Şimdi Yardımcısı sütunun değeri Mary ve hizmetine departmanı sütunun değeri değiştirildi.  
  
 Kullanıcı1 şimdi değişiklikleri gönderme çalıştığında gönderme başarısız olur ve bir <xref:System.Data.Linq.ChangeConflictException> özel durumu oluşur. Yardımcısı sütunu ve bölüm sütunu veritabanı değerlerini beklenmiyordu o olmadığından bu sonucu oluşur. Yardımcısı ve bölüm sütunları temsil eden üyeleri çakışıyor. Durumu aşağıdaki tabloda özetlenmiştir.  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|Özgün durumu|Alfreds|Maria|Satış|  
|Kullanıcı1|Alfred||Pazarlama|  
|Kullanıcı2||Mary|Hizmet|  
  
 Bu gibi farklı yollarla çakışmaları çözümleyebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: yönetmek değişiklik çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Çakışma algılamasını ve çözümleme denetim listesi  
 Algılayabilir ve ayrıntı herhangi bir düzeyde çakışmaları. Bir uçta tüm üç yöntemden birini çakışmaları (bakın <xref:System.Data.Linq.RefreshMode>) sağlayabildiği olmadan. Diğer uçta çakışma çakışan her üye üzerinde her tür için belirli bir eylemi belirlemek için kullanabilirsiniz.  
  
-   Belirtin veya düzeltmek <xref:System.Data.Linq.Mapping.UpdateCheck> nesne modelinde seçenekleri.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: belirtin üyeler eşzamanlılık çakışmalar için test](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
-   Aramanız için try/catch bloğu içinde <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, hangi noktada durum için özel durumlar istediğinizi belirtin.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: belirtin, eşzamanlılık özel durumlar](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
-   Almak istediğiniz ne kadar çakışma ayrıntısı belirlemek ve kodu buna göre try/catch bloğunda içerir.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: Varlık çakışma bilgilerini almak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) ve [nasıl yapılır: üye çakışma bilgisi almak](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md).  
  
-   Dahil, `try` / `catch` bulduğunuz çeşitli çakışmalarını çözmek istediğiniz kod.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: çakışmaları korunuyor veritabanı değerlere göre](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md), [nasıl yapılır: çakışmaları üzerine veritabanı değerlere göre](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md), ve [nasıl yapılır: çakışmaları birleştirme tarafından Veritabanı değerlerle](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md).  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>LINQ-SQL, destek çakışma bulma ve çözüm türleri  
 Sınıfları ve özellikleri iyimser eşzamanlılık çakışmalarını çözümleme desteklemek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şunları içerir:  
  
-   <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
-   <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
