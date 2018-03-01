---
title: "Yönetilen İş Parçacığı Durumları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 956472ef0e3b0bab85a4eb0b5585f1a4d1e0a991
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="managed-thread-states"></a>Yönetilen İş Parçacığı Durumları
Özellik <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> iş parçacığının geçerli durumunu belirten bir bit maskesi sağlar. Bir iş parçacığı her zaman en az bir olası durumlarda bulunduğu <xref:System.Threading.ThreadState> numaralandırma ve aynı anda birden çok durumda olabilir.  
  
> [!IMPORTANT]
>  İş parçacığı durumu olduğu yalnızca birkaç ilgi senaryoları hata ayıklama. Kodunuzu, iş parçacığı etkinliklerini eşitlemek için iş parçacığı durumu hiçbir zaman kullanmanız gerekir.  
  
 Yönetilen iş parçacığı oluşturduğunuzda, olur <xref:System.Threading.ThreadState.Unstarted> durumu. İş parçacığı kalan <xref:System.Threading.ThreadState.Unstarted> işletim sistemi tarafından başlatılan bir duruma getirilene kadar belirtin. Çağırma <xref:System.Threading.Thread.Start%2A> bilmeniz işletim sistemi sağlar iş parçacığı başlatılabilir; iş parçacığı durumu değiştirmez.  
  
 Yönetilen Ortam girin yönetilmeyen iş parçacığı zaten başlatılmış durumda. Bir iş parçacığı başlatılmış durumda olduğunda, çeşitli eylemleri durumları değiştirmek için neden olabilir. Aşağıdaki tabloda karşılık gelen yeni durum birlikte durumunun değişmesine neden eylemleri listeler.  
  
|Eylem|Sonuçta elde edilen yeni durumu|  
|------------|-------------------------|  
|Oluşturucusu <xref:System.Threading.Thread> sınıfı çağrılır.|<xref:System.Threading.ThreadState.Unstarted>|  
|Başka bir iş parçacığı çağrıları <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Unstarted>|  
|İş parçacığı yanıtlar <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> ve çalışmaya başlar.|<xref:System.Threading.ThreadState.Running>|  
|İş parçacığı çağrıları <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|İş parçacığı çağrıları <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> başka bir nesne üzerinde.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|İş parçacığı çağrıları <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> başka bir iş parçacığı üzerinde.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Başka bir iş parçacığı çağrıları <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.SuspendRequested>|  
|İş parçacığı yanıtlaması bir <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> isteği.|<xref:System.Threading.ThreadState.Suspended>|  
|Başka bir iş parçacığı çağrıları <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Running>|  
|Başka bir iş parçacığı çağrıları <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.AbortRequested>|  
|İş parçacığı yanıtlaması bir <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Aborted>, ardından<xref:System.Threading.ThreadState.Stopped>|  
  
 Çünkü <xref:System.Threading.ThreadState.Running> durumu 0 değerine sahip, bu durum bulmak için bir bit testi yapmak mümkün değildir. Bunun yerine, aşağıdaki testte (sözde kodu) kullanılabilir:  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 İş parçacığı genellikle birden fazla belirli bir zamanda durumda. Örneğin, bir iş parçacığı üzerinde engellenirse bir <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> çağrısı ve başka bir iş parçacığı çağrıları <xref:System.Threading.Thread.Abort%2A> aynı o iş parçacığı üzerinde hem de iş parçacığı olacaktır <xref:System.Threading.ThreadState.WaitSleepJoin> ve <xref:System.Threading.ThreadState.AbortRequested> aynı anda durumları. Bu durumda, iş parçacığı çağrısı döndürür hemen <xref:System.Threading.Monitor.Wait%2A> veya kesintiye, onu alırsınız <xref:System.Threading.ThreadAbortException>.  
  
 Bir iş parçacığı bırakır sonra <xref:System.Threading.ThreadState.Unstarted> yapılan bir çağrı sonucunda durum <xref:System.Threading.Thread.Start%2A>, hiçbir şekilde dönebilirsiniz <xref:System.Threading.ThreadState.Unstarted> durumu. Bir iş parçacığı hiçbir zaman ayrılmaz <xref:System.Threading.ThreadState.Stopped> durumu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)
