---
title: AutoResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38efbe0ecd88c02752d610de4b1eec8b62eca1f8
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493249"
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> Sınıf sinyal, tek bir bekleyen iş parçacığı bırakılıyor sonra otomatik olarak sıfırlanır bir yerel bekleme tanıtıcısı olayı temsil eder. Bu sınıfın temel sınıfının, özel bir durum temsil <xref:System.Threading.EventWaitHandle>. Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) kullanın ve otomatik sıfırlama olayları özellikleri için kavramsal belgelerde.  
  
 Bir <xref:System.Threading.AutoResetEvent> nesne otomatik olarak sıfırlanır için verilmemiş sistem tarafından tek bir bekleyen iş parçacığı piyasaya sürüldükten sonra. İş parçacığı bekliyorsanız, olay nesnenin durumu sinyal kalır.
  
 Kullanan bir örnek için <xref:System.Threading.AutoResetEvent>, bkz: <xref:System.Threading.Monitor>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Monitor>  
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
- [Bekleme tanıtıcıları](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
