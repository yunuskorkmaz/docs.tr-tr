---
title: 'Nasıl yapılır: Veritabanı Değerleri ile Birleştirerek Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 18a7eceeec63d9caadefab8d98942f10d82c99ca
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793357"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Nasıl yapılır: Veritabanı Değerleri ile Birleştirerek Çakışmaları Çözümleme
Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, veritabanı değerlerini geçerli istemci <xref:System.Data.Linq.RefreshMode.KeepChanges> üye değerleriyle birleştirmek için kullanabilirsiniz. Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](optimistic-concurrency-overview.md)bakış.  
  
> [!NOTE]
> Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir. Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.  
  
## <a name="example"></a>Örnek  
 Bu senaryoda, Kullanıcı1 değişiklikleri <xref:System.Data.Linq.ChangeConflictException> göndermeye çalıştığında bir özel durum oluşturulur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi. Aşağıdaki tabloda durum gösterilmektedir.  
  
||Yöneticisi|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.|Alfrelar|Maria|Satış|  
|Kullanıcı1 bu değişiklikleri göndermeye hazırlar.|Alfred||Pazarlama|  
|Kullanıcı2 bu değişiklikleri zaten gönderdi.||Mary|Hizmet|  
  
 Kullanıcı1, veritabanı değerlerini geçerli istemci üyesi değerleriyle birleştirerek bu çakışmayı çözmeye karar verir. Sonuç veritabanı değerlerinin üzerine yazılır ve yalnızca geçerli değişiklik kümesi de o değeri de değiştirmiş olur.  
  
 Kullanıcı1 kullanarak <xref:System.Data.Linq.RefreshMode.KeepChanges>çakışmayı çözdüğünde, veritabanındaki sonuç aşağıdaki tabloda olur:  
  
||Yöneticisi|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Çakışma çözümünden sonra yeni durum.|Alfred<br /><br /> (Kullanıcı1 'ten)|Mary<br /><br /> (kullanıcı2 'ten)|Pazarlama<br /><br /> (Kullanıcı1 'ten)|  
  
 Aşağıdaki örnekte, veritabanı değerlerinin geçerli istemci üye değerleriyle nasıl birleştiriyapılacağı gösterilmektedir (istemci bu değeri de değiştirmediği durumlar dışında). Tek tek üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Veritabanı değerlerinin üzerine yazarak çakışmaları çözün](how-to-resolve-conflicts-by-overwriting-database-values.md)
- [Nasıl yapılır: Veritabanı değerlerini koruyarak Çakışmaları Çöz](how-to-resolve-conflicts-by-retaining-database-values.md)
- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md)
