---
title: 'İyimser Eşzamanlılık: Genel Bakış'
ms.date: 03/30/2017
ms.assetid: c2e38512-d0c8-4807-b30a-cb7e30338694
ms.openlocfilehash: 7a1bc23d9f012b2f3541c1411a25b7527e696873
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169407"
---
# <a name="optimistic-concurrency-overview"></a>İyimser Eşzamanlılık: Genel Bakış

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] iyimser eşzamanlılık denetimini destekler. Aşağıdaki tabloda, belgelerde iyimser eşzamanlılık için uygulanan terimler açıklanmaktadır [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] :  
  
|Terimler|Açıklama|  
|-----------|-----------------|  
|eşzamanlılık|Aynı anda iki veya daha fazla kullanıcının aynı veritabanı satırını güncelleştirmeye çalıştığı durum.|  
|eşzamanlılık çakışması|Aynı anda iki veya daha fazla kullanıcının bir satırdaki bir veya daha fazla sütuna çakışan değerleri göndermeye çalıştığı durum.|  
|eşzamanlılık denetimi|Eşzamanlılık çakışmalarını çözmek için kullanılan teknik.|  
|iyimser eşzamanlılık denetimi|İlk araştırır, diğer işlemlerin, bir satırdaki değerleri, gönderilecek değişikliklere izin vermeden önce değiştirmediğini belirten tekniktir.<br /><br /> Eşzamanlılık çakışmalarını önlemek için kaydı kilitleyen, *Kötümser eşzamanlılık denetimiyle*karşıtlık.<br /><br /> *İyimser* denetim, başka bir işlemin çok az olması beklenmez bir işlem olma olasılığını düşünür.|  
|çakışma çözümleme|Veritabanını yeniden sorgulayarak ve ardından farkları mutabık tutarak çakışan bir öğeyi yenileme işlemi.<br /><br /> Bir nesne yenilendiğinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] değişiklik İzleyici aşağıdaki verileri tutar:<br /><br /> -Başlangıçta veritabanından alınan ve güncelleştirme denetimi için kullanılan değerler.<br />-Sonraki sorgudaki yeni veritabanı değerleri.<br /><br /> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ardından nesnenin çakışma durumunda olup olmadığını (yani, bir veya daha fazla üye değerinin değişip değişmediğini) belirler. Nesne çakışırsa, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir sonraki, üyelerinden hangilerinin çakışma olduğunu belirler.<br /><br /> Bulduğu herhangi bir üye çakışması [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] bir çakışma listesine eklenir.|  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Nesne modelinde, aşağıdaki koşullardan her ikisi de doğru olduğunda *iyimser eşzamanlılık çakışması* oluşur:  
  
- İstemci değişiklikleri veritabanına göndermeye çalışır.  
  
- İstemci son okuduğundan bu yana bir veya daha fazla güncelleştirme-denetim değeri veritabanında güncelleştirildi.  
  
 Bu çakışmanın çözümlenmesi, nesnenin hangi üyelerinin çakışma halinde olduğunu bulmaya ve sonra ne yapmak istediğinize karar vermenize dahildir.  
  
> [!NOTE]
> Yalnızca olarak eşleştirilen <xref:System.Data.Linq.Mapping.UpdateCheck.Always> veya <xref:System.Data.Linq.Mapping.UpdateCheck.WhenChanged> iyimser eşzamanlılık denetimlerine katılan üyeler. İşaretlenmiş Üyeler için denetim yapılmaz <xref:System.Data.Linq.Mapping.UpdateCheck.Never> . Daha fazla bilgi için bkz. <xref:System.Data.Linq.Mapping.UpdateCheck>.  
  
## <a name="example"></a>Örnek  

 Örneğin, aşağıdaki senaryoda, Kullanıcı1 bir satır için veritabanını sorgulayarak bir güncelleştirmeyi hazırlamaya başlar. Kullanıcı1, Alfreds, Maria ve Sales değerlerini içeren bir satır alır.  
  
 Kullanıcı1, yönetici sütununun değerini Alfred ve departman sütununun değerini pazarlama olarak değiştirmek istiyor. Kullanıcı1 'in bu değişiklikleri gönderebilmesi için, kullanıcı2 veritabanına değişiklikleri gönderdi. Bu nedenle, artık yardımcı sütununun değeri Mary olarak değiştirilmiştir ve departman sütununun değeri Service olarak değiştirilmiştir.  
  
 Kullanıcı1 şimdi değişiklikleri göndermeye çalıştığında, gönderim başarısız olur ve bir <xref:System.Data.Linq.ChangeConflictException> özel durum oluşturulur. Bu sonuç, yardımcı sütunu ve departman sütunu için veritabanı değerleri beklenenler olmadığı için oluşur. Yardımcı ve departman sütunlarını temsil eden Üyeler çakışıyor. Aşağıdaki tabloda durum özetlenmektedir.  
  
||Yönetici|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Özgün durum|Alfrelar|Maria|Sales|  
|Kullanıcı1|Alfred||Marketing|  
|Kullanıcı2||Mary|Hizmet|  
  
 Bu gibi çakışmaları farklı yollarla çözebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md).  
  
## <a name="conflict-detection-and-resolution-checklist"></a>Çakışma algılama ve çözümleme denetim listesi  

 Çakışmaları dilediğiniz ayrıntı düzeyinde tespit edebilir ve çözebilirsiniz. Bir Extreme 'de, her çakışmayı üç şekilde (bkz.) ek bir şekilde çözebilirsiniz <xref:System.Data.Linq.RefreshMode> . Diğer bir deyişle, çakışma içindeki her üye için her çakışma türü için belirli bir eylem belirleyebilirsiniz.  
  
- <xref:System.Data.Linq.Mapping.UpdateCheck>Nesne modelinizde seçenekleri belirtin veya gözden geçirin.  
  
     Daha fazla bilgi için bkz. [nasıl yapılır: eşzamanlılık çakışmaları Için hangi üyelerin test edildiğini belirtme](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).  
  
- Çağrın try/catch bloğunda <xref:System.Data.Linq.DataContext.SubmitChanges%2A> , özel durumların hangi noktada oluşturulması gerektiğini belirtin.  
  
     Daha fazla bilgi için bkz. [nasıl yapılır: eşzamanlılık özel durumlarının ne zaman oluşturulduğunu belirtme](how-to-specify-when-concurrency-exceptions-are-thrown.md).  
  
- Ne kadar çakışma ayrıntısı almak istediğinizi saptayın ve try/catch blobuna uygun olarak kod ekleyin.  
  
     Daha fazla bilgi için bkz. [nasıl yapılır: varlık çakışma bilgilerini alma](how-to-retrieve-entity-conflict-information.md) ve [nasıl yapılır: üye çakışma bilgilerini alma](how-to-retrieve-member-conflict-information.md).  
  
- `try` / `catch` Keşfettiğiniz çeşitli çakışmaları nasıl çözümlemek istediğinizi kodunuza ekleyin.  
  
     Daha fazla bilgi için bkz. [nasıl yapılır: veritabanı değerlerini koruyarak çakışmaları çözme](how-to-resolve-conflicts-by-retaining-database-values.md), [nasıl yapılır: veritabanı değerlerini üzerine yazarak çakışmaları](how-to-resolve-conflicts-by-overwriting-database-values.md)çözme ve [nasıl yapılır: veritabanı değerleriyle birleştirerek çakışmaları](how-to-resolve-conflicts-by-merging-with-database-values.md)çözme.  
  
## <a name="linq-to-sql-types-that-support-conflict-discovery-and-resolution"></a>Çakışma bulmayı ve çözümlemeyi destekleyen LINQ to SQL türleri  

 ' De iyimser eşzamanlılık içindeki çakışmaların çözümlenmesini desteklemeye yönelik sınıflar ve özellikler şunları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] içerir:  
  
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

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
