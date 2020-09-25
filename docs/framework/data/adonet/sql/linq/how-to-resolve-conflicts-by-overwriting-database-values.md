---
title: 'Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 1dc112350451bde28d27c63961733b96f6fc84be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191716"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme

Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> veritabanı değerlerinin üzerine yazmak için kullanabilirsiniz. Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).  
  
> [!NOTE]
> Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir. Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.  
  
## <a name="example"></a>Örnek  

 Bu senaryoda, <xref:System.Data.Linq.ChangeConflictException> kullanıcı1 değişiklikleri göndermeye çalıştığında bir özel durum oluşur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi. Aşağıdaki tabloda durum gösterilmektedir.  
  
||Yönetici|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.|Alfrelar|Maria|Sales|  
|Kullanıcı1 bu değişiklikleri göndermeye hazırlar.|Alfred||Marketing|  
|Kullanıcı2 bu değişiklikleri zaten gönderdi.||Mary|Hizmet|  
  
 Kullanıcı1, geçerli istemci üyesi değerleri ile veritabanı değerlerinin üzerine yazarak bu çakışmayı çözmeye karar verir.  
  
 Kullanıcı1 kullanarak çakışmayı çözdüğünde <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> , veritabanındaki sonuç aşağıdaki tabloda olur:  
  
||Yönetici|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Çakışma çözümünden sonra yeni durum.|Alfred<br /><br /> (Kullanıcı1 'ten)|Maria<br /><br /> orijinale|Marketing<br /><br /> (Kullanıcı1 'ten)|  
  
 Aşağıdaki örnek kod, geçerli istemci üyesi değerleri ile veritabanı değerlerinin üzerine yazmayı gösterir. (Bireysel üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
