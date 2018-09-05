---
title: Saniyede Akışı Yapılan İşlem
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501310"
---
# <a name="transactions-flowed-per-second"></a>Saniyede Akışı Yapılan İşlem
Sayaç adı: Saniye başına işlemler  
  
## <a name="description"></a>Açıklama  
 İşlem sayısı, bu işleme bir saniye içinde aktarılan. İşlem kimliği mevcut işleme gönderilen bir iletinin dilediğiniz zaman bu sayaç artırılır.  
  
 Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
