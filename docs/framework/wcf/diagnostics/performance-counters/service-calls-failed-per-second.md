---
description: 'Şu konuda daha fazla bilgi edinin: hizmet: başarısız çağrı/saniye'
title: 'Hizmet: Saniyede Başarısız Olan Çağrı'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: b271d5076d0f0c89c4d33b124e0184584795466a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803366"
---
# <a name="service-calls-failed-per-second"></a>Hizmet: Saniyede Başarısız Olan Çağrı

Sayaç adı: saniye başına başarısız çağrı.  
  
## <a name="description"></a>Description  

 İşlenmemiş özel durumlara sahip ve bu hizmet tarafından bir saniyede alınan çağrıların sayısı.  
  
 Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur.  
  
 Yönetilen kodda, hata koşulları oluştuğunda özel durumlar oluşturulur.  
  
 Bu hizmette işlenmeyen bir özel durum olduğunda bu sayaç artırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Sözleşme ve Hizmetlerde Hataları Belirtme ve İşleme](../../specifying-and-handling-faults-in-contracts-and-services.md)
