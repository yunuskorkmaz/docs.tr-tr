---
title: "Nasıl yapılır: çakışmaları veritabanı değerlerle birleştirerek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ee1016a6dc20e58bfafc434617a36f8f8703a3bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a>Nasıl yapılır: çakışmaları veritabanı değerlerle birleştirerek
Değişikliklerinizi yeniden denemeden önce beklenen ve mevcut veritabanı değerleri arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.KeepChanges> geçerli istemci üye değerlerle veritabanı değerleri birleştirmek için. Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak ilk yenilenir. Bu eylem sonraki güncelleştirme deneyin üzerinde aynı tutarlılık denetimleri başarısız olmayan emin olur.  
  
## <a name="example"></a>Örnek  
 Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 zarfında Yardımcısı ve bölüm sütunları değiştiği için değişiklikleri göndermek Kullanıcı1 çalıştığında özel durum. Aşağıdaki tabloda durumu gösterir.  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında, orijinal veritabanı durumu.|Alfreds|Maria|Satış|  
|Bu değişiklikleri göndermek Kullanıcı1 hazırlar.|Alfred||Pazarlama|  
|Kullanıcı2 zaten bu değişiklikleri gönderdi.||Mary|Hizmet|  
  
 Kullanıcı1 veritabanı değerlerini geçerli istemci üye değerlerle birleştirerek Bu çakışmayı karar verir. Sonucu, geçerli değişiklik kümesi de değiştirilmiş bu değer yalnızca değerleri üzerine yazılır veritabanının olacaktır.  
  
 Ne zaman Kullanıcı1 çözümler çakışma kullanarak <xref:System.Data.Linq.RefreshMode.KeepChanges>, sonuç veritabanında olduğu gibi aşağıdaki tabloda gösterilmiştir:  
  
||Yöneticisi|Yardımcısı|Bölüm|  
|------|-------------|---------------|----------------|  
|Yeni durum çakışma çözümü sonra.|Alfred<br /><br /> (kullanıcı1)|Mary<br /><br /> (kullanıcı2)|Pazarlama<br /><br /> (kullanıcı1)|  
  
 Aşağıdaki örnek, geçerli istemci üye değerlerle veritabanı değerleri (istemci de bu değeri değiştirilmediği sürece) birleştirmek gösterilmiştir. Hiçbir denetleme veya tek tek üye çakışmalarını özel işleme oluşur.  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 [Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 [Nasıl yapılır: Değişiklik Çakışmalarını Yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
