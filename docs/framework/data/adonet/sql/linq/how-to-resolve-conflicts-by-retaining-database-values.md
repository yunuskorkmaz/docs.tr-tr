---
title: 'Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: 8440ffe61e254403357970d771aea207a6eb6092
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59230115"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a>Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme
Değişikliklerinizi yeniden denemeden önce veritabanı beklenen ve gerçek değerler arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> veritabanında bulunan değerlerini korumak için. Nesne modelinde geçerli değerlerin üzerine yazılır. Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak önce yenilenir. Bu eylem, İleri güncelleştirmeyi deneyin üzerinde aynı eşzamanlılık denetimlerinin dönmüyor emin olur.  
  
## <a name="example"></a>Örnek  
 Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 sırada Yardımcısı ve bölüm sütunları değiştiğinden, değişiklikleri göndermek User1 çalıştığında özel durum harekete geçirilir. Aşağıdaki tablo, durumu gösterir.  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|User1 ve kullanıcı2 tarafından sorgulandığında, özgün veritabanının durumu.|Alfreds|Maria|Satış|  
|Kullanıcı1, bu değişiklikleri göndermek hazırlar.|Alfred||Pazarlama|  
|Kullanıcı2 bu değişiklikleri zaten gönderildi.||Mary|Hizmet|  
  
 User1 nesne modelinde geçerli değerlerin üzerine daha yeni veritabanı değerleri sağlayarak bu çakışmayı karar verir.  
  
 Ne zaman User1 çözümlenen çakışması kullanarak <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, sonuç veritabanındaki tabloda aşağıdaki gibidir:  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|Çakışma çözümü sonra yeni durumu.|Alfreds<br /><br /> (özgün)|Mary<br /><br /> (kullanıcı2)|Hizmet<br /><br /> (kullanıcı2)|  
  
 Aşağıdaki kod örneği, veritabanı değerleri ile nesne modelinde geçerli değerlerin üzerine gösterilmektedir. (Herhangi bir inceleme veya tek tek üye çakışıyor özel işleme gerçekleşir.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
