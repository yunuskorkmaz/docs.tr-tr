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
ms.openlocfilehash: a4ab06993eed4b39746875a6ef3ebfad5edbd2e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581709"
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> Sınıfı işaret, tek bir bekleyen iş parçacığı bırakılıyor sonra olduğunda otomatik olarak sıfırlar yerel bekleme tanıtıcısı olayı temsil eder. Bu sınıf temel sınıfı olan özel bir durum gösteren <xref:System.Threading.EventWaitHandle>. Bkz: [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) kullanım ve otomatik sıfırlama olayları özelliklerini kavramsal belgeler.  
  
 Bir <xref:System.Threading.AutoResetEvent> nesne otomatik olarak sıfırlanır çok işaret olmayan sistem tarafından tek bir bekleyen iş parçacığı serbest bırakıldıktan sonra. İş parçacığı bekleyen olay nesnenin durumu iş olarak kalır. <xref:System.Threading.AutoResetEvent> Win32 öğesine karşılık gelen `CreateEvent` çağrısı, belirtme `false` için `bManualReset` bağımsız değişkeni.  
  
 Kullanan bir örnek <xref:System.Threading.AutoResetEvent>, bkz: [İzleyici](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Bekleme tanıtıcıları](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
