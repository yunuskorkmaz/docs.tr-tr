---
title: 'Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: f6721234d2d3920343bc72889c7683fb6ee662a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928765"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme
Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, veritabanı değerlerinin üzerine yazmak <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> için kullanabilirsiniz. Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)bakış.  
  
> [!NOTE]
> Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir. Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.  
  
## <a name="example"></a>Örnek  
 Bu senaryoda, Kullanıcı1 değişiklikleri <xref:System.Data.Linq.ChangeConflictException> göndermeye çalıştığında bir özel durum oluşur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi. Aşağıdaki tabloda durum gösterilmektedir.  
  
||Yöneticisi|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.|Alfrelar|Maria|Satış|  
|Kullanıcı1 bu değişiklikleri göndermeye hazırlar.|Alfred||Pazarlama|  
|Kullanıcı2 bu değişiklikleri zaten gönderdi.||Mary|Hizmet|  
  
 Kullanıcı1, geçerli istemci üyesi değerleri ile veritabanı değerlerinin üzerine yazarak bu çakışmayı çözmeye karar verir.  
  
 Kullanıcı1 kullanarak <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>çakışmayı çözdüğünde, veritabanındaki sonuç aşağıdaki tabloda olur:  
  
||Yöneticisi|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Çakışma çözümünden sonra yeni durum.|Alfred<br /><br /> (Kullanıcı1 'ten)|Maria<br /><br /> orijinale|Pazarlama<br /><br /> (Kullanıcı1 'ten)|  
  
 Aşağıdaki örnek kod, geçerli istemci üyesi değerleri ile veritabanı değerlerinin üzerine yazmayı gösterir. (Bireysel üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
