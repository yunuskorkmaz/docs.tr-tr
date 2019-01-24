---
title: 'Nasıl yapılır: Veritabanı değerlerinin üzerine yazarak çakışmaları'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 38129996949bcfbd938038743897d1db5910fdfe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653914"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a>Nasıl yapılır: Veritabanı değerlerinin üzerine yazarak çakışmaları
Değişikliklerinizi yeniden denemeden önce veritabanı beklenen ve gerçek değerler arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> veritabanı değerlerinin üzerine yazmak için. Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak önce yenilenir. Bu eylem, İleri güncelleştirmeyi deneyin üzerinde aynı eşzamanlılık denetimlerinin dönmüyor emin olur.  
  
## <a name="example"></a>Örnek  
 Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 sırada Yardımcısı ve bölüm sütunları değiştiğinden, değişiklikleri göndermek User1 çalıştığında özel durum harekete geçirilir. Aşağıdaki tablo, durumu gösterir.  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|User1 ve kullanıcı2 tarafından sorgulandığında, özgün veritabanının durumu.|Alfreds|Maria|Satış|  
|Kullanıcı1, bu değişiklikleri göndermek hazırlar.|Alfred||Pazarlama|  
|Kullanıcı2 bu değişiklikleri zaten gönderildi.||Mary|Hizmet|  
  
 User1 geçerli istemci üye değerlerle veritabanı değerlerinin üzerine yazarak bu çakışmayı karar verir.  
  
 Ne zaman User1 çözümlenen çakışması kullanarak <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, sonuç veritabanında olduğu gibi aşağıdaki tabloda gösterilmiştir:  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|Çakışma çözümü sonra yeni durumu.|Alfred<br /><br /> (kullanıcı1)|Maria<br /><br /> (özgün)|Pazarlama<br /><br /> (kullanıcı1)|  
  
 Aşağıdaki kod örneği, geçerli istemci üye değerlerle veritabanı değerlerinin üzerine gösterilmektedir. (Herhangi bir inceleme veya tek tek üye çakışıyor özel işleme gerçekleşir.)  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
