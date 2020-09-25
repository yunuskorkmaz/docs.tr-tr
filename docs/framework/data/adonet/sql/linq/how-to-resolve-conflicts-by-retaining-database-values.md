---
title: 'Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: b6f9b0308bcbf53a89ae0690ed44db0a364aef0c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191703"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme

Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> veritabanında bulunan değerleri bekletmek için kullanabilirsiniz. Nesne modelindeki geçerli değerlerin üzerine yazılır. Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).  
  
> [!NOTE]
> Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir. Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.  
  
## <a name="example"></a>Örnek  

 Bu senaryoda, <xref:System.Data.Linq.ChangeConflictException> kullanıcı1 değişiklikleri göndermeye çalıştığında bir özel durum oluşturulur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi. Aşağıdaki tabloda durum gösterilmektedir.  
  
||Yönetici|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.|Alfrelar|Maria|Sales|  
|Kullanıcı1 bu değişiklikleri göndermeye hazırlar.|Alfred||Marketing|  
|Kullanıcı2 bu değişiklikleri zaten gönderdi.||Mary|Hizmet|  
  
 Kullanıcı1, daha yeni veritabanı değerlerini nesne modelindeki geçerli değerlerin üzerine yazarak bu çakışmayı çözmeye karar verir.  
  
 Kullanıcı1 kullanarak çakışmayı çözdüğünde <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> , veritabanındaki sonuç tabloda aşağıdaki gibidir:  
  
||Yönetici|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Çakışma çözümünden sonra yeni durum.|Alfrelar<br /><br /> orijinale|Mary<br /><br /> (kullanıcı2 'ten)|Hizmet<br /><br /> (kullanıcı2 'ten)|  
  
 Aşağıdaki örnek kod, veritabanı değerleriyle nesne modelindeki geçerli değerlerin üzerine yazmayı gösterir. (Bireysel üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
