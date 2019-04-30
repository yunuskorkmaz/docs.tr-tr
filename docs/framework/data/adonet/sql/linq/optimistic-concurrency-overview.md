---
title: 'İyimser Eşzamanlılık: Genel Bakış'
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: 8f3bd35cc1391339d99d5aa0a4021e29fa81756c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767500"
---
# <a name="optimistic-concurrency-overview"></a>İyimser Eşzamanlılık: Genel Bakış
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] İyimser eşzamanlılık denetimini destekler. Aşağıdaki tabloda iyimser eşzamanlılık uygulamak terimleri açıklanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] belgeleri:  
  
|Koşulları|Açıklama|  
|-----------|-----------------|  
|eşzamanlılık|İki veya daha fazla kullanıcı aynı anda aynı veritabanına satırı güncelleştirmek deneyin durumu.|  
|Eşzamanlılık çakışması|İki veya daha fazla kullanıcı aynı anda bir veya daha fazla sütun bir satır için çakışan değerleri göndermek deneyin durumu.|  
|eşzamanlılık denetimi|Eşzamanlılık çakışmalarını çözümlemek için kullanılan yöntem.|  
|İyimser eşzamanlılık denetimi|İlk değişiklikleri ayrılmak üzere gönderilmesine izin veren önce diğer işlemleri bir satır değerleri değişip değişmediğini araştırır tekniğidir.<br /><br /> İle Karşıtlık *kötümser eşzamanlılık denetimi*, eşzamanlılık çakışmalarını önlemek için kayıt kilitler.<br /><br /> *İyimser* denetimi bir işlem başka olası olacak şekilde müdahale etmeden olasılığını varsaydığı şekilde ifade.|  
|Çakışma çözümü|Çakışan öğe yenilenmesini veritabanını yeniden sorgulama ve ardından farkları mutabık kılma işlemi.<br /><br /> Bir nesne yenilendiğinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişikliği İzleyicisi aşağıdaki veri tutar:<br /><br /> -İlk olarak veritabanından alınan ve kullanılan güncelleştirmesi değerleri kontrol edin.<br />-Yeni veritabanı değerlerini izleyen sorgu.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Ardından, nesne çakışan (diğer bir deyişle, bir veya daha fazla üye değerlerinin değiştirilip) olup olmadığını belirler. Çakışan nesne ise [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sonraki çakışma içinde olan üyelerinin belirler.<br /><br /> Herhangi bir üye çakışma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bulur bir çakışma listesine eklenir.|  
  
 İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nesne modeli, bir *iyimser eşzamanlılık çakışması* aşağıdaki koşulların her ikisinin de doğru olduğunda oluşur:  
  
- İstemci, veritabanına değişiklikleri gönderme dener.  
  
- İstemcinin en son bunları okumak bu yana veritabanında bir veya daha fazla güncelleştirme denetimi değerler güncelleştirildi.  
  
 Bu çakışma çözümlemesi çakışma nesnenin hangi üyelerin bulmak ve ardından bunu yapmak istediğinize karar içerir.  
  
> [!NOTE]
>  Yalnızca üyeleri eşleştirilmiş olarak <xref:System.Data.Linq.Mapping.UpdateCheck.Always> veya <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> iyimser eşzamanlılık denetimlerini katılın. Onay için işaretlenen üyelerin gerçekleştirilir <xref:System.Data.Linq.Mapping.UpdateCheck.Never>. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Örnek  
 Örneğin, aşağıdaki senaryoda, bir satır için veritabanını sorgulayarak bir güncelleştirme hazırlamak User1 başlatır. User1 Alfreds, Maria ve satış değerleri içeren bir satır alır.  
  
 User1 Alfred ve pazarlama departmanı sütununun değerini Manager sütununun değerini değiştirmek istiyor. User1 bu değişiklikleri gönderebilmeniz için önce kullanıcı2 veritabanında yapılan değişiklikler gönderdi. Şimdi Yardımcısı sütununun değeri, Gamze ve hizmet için bölüm sütununun değeri değiştirildi.  
  
 Gönderim user1 şimdi değişiklikleri gönderme çalıştığında başarısız ve <xref:System.Data.Linq.ChangeConflictException> özel durumu oluşturulur. Veritabanı değerlerin Yardımcısı sütunu ve bölüm sütunu için beklenmiyordu o olmadığından bu sonucu oluşur. Üyeleri Yardımcısı ve bölüm sütunları temsil eden çakışıyor. Durum aşağıdaki tabloda özetlenmiştir.  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|Özgün durumuna|Alfreds|Maria|Satış|  
|user1|Alfred||Pazarlama|  
|Kullanıcı2||Mary|Hizmet|  
  
 Bu gibi çakışmaları farklı şekilde çözebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Çakışma algılama ve çözümleme denetim listesi  
 Algılayın ve herhangi bir düzeyde ayrıntı çakışmaları çözün. Bir uçta üç yoldan biriyle bütün çakışmaları çözün (bkz <xref:System.Data.Linq.RefreshMode>) sağlayabildiği olmadan. Diğer uçta her üye çakışma içinde çakışma oluştu her türü için belirli bir eylemi belirleyebilirsiniz.  
  
- Belirtin veya düzeltmek <xref:System.Data.Linq.Mapping.UpdateCheck> , nesne modelinde seçenekleri.  
  
     Daha fazla bilgi için [nasıl yapılır: Hangi üyelerin eşzamanlılık çakışmaları için test edildiğini belirtme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
- Try/catch bloğunda, çağrınız <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, hangi noktada özel durum oluşturulmasına istediğinizi belirtin.  
  
     Daha fazla bilgi için [nasıl yapılır: Zaman eşzamanlılık özel durum belirtin](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
- Almak istediğiniz kadar çakışma ayrıntının belirleme ve kodu uygun şekilde, try/catch bloğu içinde içerir.  
  
     Daha fazla bilgi için [nasıl yapılır: Varlık çakışma bilgilerini alma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) ve [nasıl yapılır: Üye çakışma bilgilerini alma](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md).  
  
- Dahil, `try` / `catch` nasıl bulduğunuz çeşitli çakışmaları çözümlemek istediğiniz kodu.  
  
     Daha fazla bilgi için [nasıl yapılır: Veritabanı değerlerini tutarak çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md), [nasıl yapılır: Veritabanı değerlerinin üzerine yazarak çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md), ve [nasıl yapılır: Veritabanı değerleri ile birleştirerek çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md).  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>LINQ to SQL türleri, çakışma bulma ve çözümleme desteği  
 Sınıfları ve özellikleri iyimser eşzamanlılık çakışmaları çözümleme desteklemek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] şunları içerir:  
  
- <xref:System.Data.Linq.ObjectChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.MemberChangeConflict?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictCollection?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.ChangeConflictException?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.ChangeConflicts%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.SubmitChanges%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.DataContext.Refresh%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.Mapping.UpdateCheck?displayProperty=nameWithType>  
  
- <xref:System.Data.Linq.RefreshMode?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
