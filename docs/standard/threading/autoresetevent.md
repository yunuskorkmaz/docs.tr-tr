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
ms.openlocfilehash: 519776b5c1c237deb520476384495b8dd96a4e39
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50039289"
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> Sınıf sinyal, tek bir bekleyen iş parçacığı bırakılıyor sonra otomatik olarak sıfırlanır bir yerel bekleme tanıtıcısı olayı temsil eder. Bu sınıfın temel sınıfının, özel bir durum temsil <xref:System.Threading.EventWaitHandle>. Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) kullanın ve otomatik sıfırlama olayları özellikleri için kavramsal belgelerde.  
  
 Bir <xref:System.Threading.AutoResetEvent> nesne otomatik olarak sıfırlanır için verilmemiş sistem tarafından tek bir bekleyen iş parçacığı piyasaya sürüldükten sonra. İş parçacığı bekliyorsanız, olay nesnenin durumu sinyal kalır.
  
 Kullanan bir örnek için <xref:System.Threading.AutoResetEvent>, bkz: <xref:System.Threading.Monitor>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)  
- [İş parçacığı oluşturma](index.md)  
