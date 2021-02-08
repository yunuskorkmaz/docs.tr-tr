---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: veritabanı değerleriyle birleştirerek çakışmaları çözme'
title: 'Nasıl yapılır: Veritabanı Değerleri ile Birleştirerek Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 83cae4c98fdd2e51065c66d36ef04202bdc86c9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767771"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Nasıl yapılır: Veritabanı Değerleri ile Birleştirerek Çakışmaları Çözümleme

Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, <xref:System.Data.Linq.RefreshMode.KeepChanges> veritabanı değerlerini geçerli istemci üye değerleriyle birleştirmek için kullanabilirsiniz. Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).  
  
> [!NOTE]
> Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir. Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.  
  
## <a name="example"></a>Örnek  

 Bu senaryoda, <xref:System.Data.Linq.ChangeConflictException> kullanıcı1 değişiklikleri göndermeye çalıştığında bir özel durum oluşturulur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi. Aşağıdaki tabloda durum gösterilmektedir.  
  
||Yönetici|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.|Alfrelar|Maria|Sales|  
|Kullanıcı1 bu değişiklikleri göndermeye hazırlar.|Alfred||Marketing|  
|Kullanıcı2 bu değişiklikleri zaten gönderdi.||Mary|Hizmet|  
  
 Kullanıcı1, veritabanı değerlerini geçerli istemci üyesi değerleriyle birleştirerek bu çakışmayı çözmeye karar verir. Sonuç veritabanı değerlerinin üzerine yazılır ve yalnızca geçerli değişiklik kümesi de o değeri de değiştirmiş olur.  
  
 Kullanıcı1 kullanarak çakışmayı çözdüğünde <xref:System.Data.Linq.RefreshMode.KeepChanges> , veritabanındaki sonuç aşağıdaki tabloda olur:  
  
||Yönetici|Yardımc|Bölüm|  
|------|-------------|---------------|----------------|  
|Çakışma çözümünden sonra yeni durum.|Alfred<br /><br /> (Kullanıcı1 'ten)|Mary<br /><br /> (kullanıcı2 'ten)|Marketing<br /><br /> (Kullanıcı1 'ten)|  
  
 Aşağıdaki örnekte, veritabanı değerlerinin geçerli istemci üye değerleriyle nasıl birleştiriyapılacağı gösterilmektedir (istemci bu değeri de değiştirmediği durumlar dışında). Tek tek üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme](how-to-resolve-conflicts-by-overwriting-database-values.md)
- [Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme](how-to-resolve-conflicts-by-retaining-database-values.md)
- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](how-to-manage-change-conflicts.md)
