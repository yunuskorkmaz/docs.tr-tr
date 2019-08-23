---
title: 'İyimser Eşzamanlılık: Genel Bakış'
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: a61d4c5b35f3797539fe845045b8a959b0351350
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938625"
---
# <a name="optimistic-concurrency-overview"></a>İyimser Eşzamanlılık: Genel Bakış
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]iyimser eşzamanlılık denetimini destekler. Aşağıdaki tabloda, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] belgelerde iyimser eşzamanlılık için uygulanan terimler açıklanmaktadır:  
  
|Larındaki|Açıklama|  
|-----------|-----------------|  
|eşzamanlılık|Aynı anda iki veya daha fazla kullanıcının aynı veritabanı satırını güncelleştirmeye çalıştığı durum.|  
|eşzamanlılık çakışması|Aynı anda iki veya daha fazla kullanıcının bir satırdaki bir veya daha fazla sütuna çakışan değerleri göndermeye çalıştığı durum.|  
|eşzamanlılık denetimi|Eşzamanlılık çakışmalarını çözmek için kullanılan teknik.|  
|iyimser eşzamanlılık denetimi|İlk araştırır, diğer işlemlerin, bir satırdaki değerleri, gönderilecek değişikliklere izin vermeden önce değiştirmediğini belirten tekniktir.<br /><br /> Eşzamanlılık çakışmalarını önlemek için kaydı kilitleyen, *Kötümser eşzamanlılık denetimiyle*karşıtlık.<br /><br /> *İyimser* denetim, başka bir işlemin çok az olması beklenmez bir işlem olma olasılığını düşünür.|  
|çakışma çözümleme|Veritabanını yeniden sorgulayarak ve ardından farkları mutabık tutarak çakışan bir öğeyi yenileme işlemi.<br /><br /> Bir nesne yenilendiğinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişiklik İzleyici aşağıdaki verileri tutar:<br /><br /> -Başlangıçta veritabanından alınan ve güncelleştirme denetimi için kullanılan değerler.<br />-Sonraki sorgudaki yeni veritabanı değerleri.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ardından nesnenin çakışma durumunda olup olmadığını (yani, bir veya daha fazla üye değerinin değişip değişmediğini) belirler. Nesne çakışırsa, bir sonraki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] üyelerinden hangilerinin çakışma olduğunu belirler.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bulduğu herhangi bir üye çakışması bir çakışma listesine eklenir.|  
  
 Nesne modelinde, aşağıdaki koşullardan her ikisi de doğru olduğunda *iyimser eşzamanlılık çakışması* oluşur: [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
- İstemci değişiklikleri veritabanına göndermeye çalışır.  
  
- İstemci son okuduğundan bu yana bir veya daha fazla güncelleştirme-denetim değeri veritabanında güncelleştirildi.  
  
 Bu çakışmanın çözümlenmesi, nesnenin hangi üyelerinin çakışma halinde olduğunu bulmaya ve sonra ne yapmak istediğinize karar vermenize dahildir.  
  
> [!NOTE]
> Yalnızca olarak <xref:System.Data.Linq.Mapping.UpdateCheck.Always> eşleştirilen veya <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> iyimser eşzamanlılık denetimlerine katılan üyeler. İşaretlenmiş <xref:System.Data.Linq.Mapping.UpdateCheck.Never>Üyeler için denetim yapılmaz. Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Örnek  
 Örneğin, aşağıdaki senaryoda, Kullanıcı1 bir satır için veritabanını sorgulayarak bir güncelleştirmeyi hazırlamaya başlar. Kullanıcı1, Alfreds, Maria ve Sales değerlerini içeren bir satır alır.  
  
 Kullanıcı1, yönetici sütununun değerini Alfred ve departman sütununun değerini pazarlama olarak değiştirmek istiyor. Kullanıcı1 'in bu değişiklikleri gönderebilmesi için, kullanıcı2 veritabanına değişiklikleri gönderdi. Bu nedenle, artık yardımcı sütununun değeri Mary olarak değiştirilmiştir ve departman sütununun değeri Service olarak değiştirilmiştir.  
  
 Kullanıcı1 şimdi değişiklikleri göndermeye çalıştığında, gönderim başarısız olur ve bir <xref:System.Data.Linq.ChangeConflictException> özel durum oluşturulur. Bu sonuç, yardımcı sütunu ve departman sütunu için veritabanı değerleri beklenenler olmadığı için oluşur. Yardımcı ve departman sütunlarını temsil eden Üyeler çakışıyor. Aşağıdaki tabloda durum özetlenmektedir.  
  
||Yöneticisi|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Özgün durum|Alfrelar|Maria|Satış|  
|Kullanıcı1|Alfred||Pazarlama|  
|Kullanıcı2||Mary|Hizmet|  
  
 Bu gibi çakışmaları farklı yollarla çözebilirsiniz. Daha fazla bilgi için [nasıl yapılır: Değişiklik çakışmalarını](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)yönetin.  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Çakışma algılama ve çözümleme denetim listesi  
 Çakışmaları dilediğiniz ayrıntı düzeyinde tespit edebilir ve çözebilirsiniz. Bir Extreme 'de, her çakışmayı üç şekilde (bkz <xref:System.Data.Linq.RefreshMode>.) ek bir şekilde çözebilirsiniz. Diğer bir deyişle, çakışma içindeki her üye için her çakışma türü için belirli bir eylem belirleyebilirsiniz.  
  
- Nesne modelinizde <xref:System.Data.Linq.Mapping.UpdateCheck> seçenekleri belirtin veya gözden geçirin.  
  
     Daha fazla bilgi için [nasıl yapılır: Eşzamanlılık çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)Için hangi üyelerin test edildiğini belirtin.  
  
- Çağrın try/catch bloğunda <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, özel durumların hangi noktada oluşturulması gerektiğini belirtin.  
  
     Daha fazla bilgi için [nasıl yapılır: Eşzamanlılık özel durumlarının ne zaman oluşturulur](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)belirtin.  
  
- Ne kadar çakışma ayrıntısı almak istediğinizi saptayın ve try/catch blobuna uygun olarak kod ekleyin.  
  
     Daha fazla bilgi için [nasıl yapılır: Varlık çakışma bilgilerini](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md) alın ve [şunları yapın: Üye çakışma bilgilerini](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)alın.  
  
- Keşfettiğiniz çeşitli çakışmaları nasıl çözümlemek istediğinizi kodunuzaekleyin.`catch` `try` /  
  
     Daha fazla bilgi için [nasıl yapılır: Veritabanı değerlerini](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)koruyarak çakışmaları çözümleyin, [nasıl yapılır: Veritabanı değerlerinin](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)üzerine yazarak çakışmaları çözün ve [şunları yapın: Veritabanı değerleriyle](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)birleştirerek çakışmaları çözün.  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>Çakışma bulmayı ve çözümlemeyi destekleyen LINQ to SQL türleri  
 ' De [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iyimser eşzamanlılık içindeki çakışmaların çözümlenmesini desteklemeye yönelik sınıflar ve özellikler şunları içerir:  
  
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
