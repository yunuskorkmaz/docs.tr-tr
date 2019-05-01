---
title: Saniyede Akışı Yapılan İşlem
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927198"
---
# <a name="transactions-flowed-per-second"></a>Saniyede Akışı Yapılan İşlem
Sayaç adı:  Saniyede Akışı Yapılan İşlem  
  
## <a name="description"></a>Açıklama  
 İşlem sayısı, bu işleme bir saniye içinde aktarılan. İşlem kimliği mevcut işleme gönderilen bir iletinin dilediğiniz zaman bu sayaç artırılır.  
  
 Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.  
  
 (1 - N 0 N) / ((D 1 - D 0) / F)
