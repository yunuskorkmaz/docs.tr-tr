---
title: 'Nasıl yapılır: Veritabanı değerleri ile birleştirerek çakışmaları'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 2b6daa28c23c74eaea21f1f3d499a2e206252abd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744134"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Nasıl yapılır: Veritabanı değerleri ile birleştirerek çakışmaları
Değişikliklerinizi yeniden denemeden önce veritabanı beklenen ve gerçek değerler arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.KeepChanges> veritabanı değerleri geçerli istemci üye değerleri birleştirecek. Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak önce yenilenir. Bu eylem, İleri güncelleştirmeyi deneyin üzerinde aynı eşzamanlılık denetimlerinin dönmüyor emin olur.  
  
## <a name="example"></a>Örnek  
 Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 sırada Yardımcısı ve bölüm sütunları değiştiğinden, değişiklikleri göndermek User1 çalıştığında özel durum harekete geçirilir. Aşağıdaki tablo, durumu gösterir.  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|User1 ve kullanıcı2 tarafından sorgulandığında, özgün veritabanının durumu.|Alfreds|Maria|Satış|  
|Kullanıcı1, bu değişiklikleri göndermek hazırlar.|Alfred||Pazarlama|  
|Kullanıcı2 bu değişiklikleri zaten gönderildi.||Mary|Hizmet|  
  
 User1 veritabanı değerleri geçerli istemci üye değerleri ile birleştirerek Bu çakışmayı karar verir. Sonucu, geçerli değişiklik kümesi de değiştirilmiş bu değer yalnızca değerlerin üzerine yazılır veritabanı olacaktır.  
  
 Ne zaman User1 çözümlenen çakışması kullanarak <xref:System.Data.Linq.RefreshMode.KeepChanges>, sonuç veritabanında olduğu gibi aşağıdaki tabloda gösterilmiştir:  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|Çakışma çözümü sonra yeni durumu.|Alfred<br /><br /> (kullanıcı1)|Mary<br /><br /> (kullanıcı2)|Pazarlama<br /><br /> (kullanıcı1)|  
  
 Aşağıdaki örnek, veritabanı değerlerini geçerli istemci üye değerler ile (istemci de bu değeri değiştirilmediği sürece) birleştirme gösterilmektedir. İnceleme ya da tek tek üye çakışıyor özel işleme gerçekleşir.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Veritabanı değerlerinin üzerine yazarak çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)
- [Nasıl yapılır: Veritabanı değerlerini tutarak çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)
- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
