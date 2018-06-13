---
title: 'Nasıl yapılır: çakışmaları veritabanı değerlerini koruyarak'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: d0d59c520beaab2d6c8c1594ee81a3eaecf1d03e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33361701"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Nasıl yapılır: çakışmaları veritabanı değerlerini koruyarak
Değişikliklerinizi yeniden denemeden önce beklenen ve mevcut veritabanı değerleri arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> veritabanında bulunan değerleri korumak için. Nesne modeli geçerli değerleri ardından üzerine yazılır. Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak ilk yenilenir. Bu eylem sonraki güncelleştirme deneyin üzerinde aynı tutarlılık denetimleri başarısız olmayan emin olur.  
  
## <a name="example"></a>Örnek  
 Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 zarfında Yardımcısı ve bölüm sütunları değiştiği için değişiklikleri göndermek Kullanıcı1 çalıştığında özel durum. Aşağıdaki tabloda durumu gösterir.  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında, orijinal veritabanı durumu.|Alfreds|Maria|Satış|  
|Bu değişiklikleri göndermek Kullanıcı1 hazırlar.|Alfred||Pazarlama|  
|Kullanıcı2 zaten bu değişiklikleri gönderdi.||Mary|Hizmet|  
  
 Kullanıcı1 nesne modeli geçerli değerleri üzerine daha yeni veritabanı değerlerini sağlayarak bu çakışmayı karar verir.  
  
 Ne zaman Kullanıcı1 çözümler çakışma kullanarak <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, veritabanı sonucunda tabloda aşağıdaki gibidir:  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|Yeni durum çakışma çözümü sonra.|Alfreds<br /><br /> (orijinal)|Mary<br /><br /> (kullanıcı2)|Hizmet<br /><br /> (kullanıcı2)|  
  
 Aşağıdaki kod örneği, nesne modelinde geçerli değerleri veritabanı değerlerle üzerine gösterilmektedir. (Hiçbir denetleme veya tek tek üye çakışmalarını özel işleme gerçekleşir.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
