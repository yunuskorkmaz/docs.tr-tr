---
title: Yönetilen İş Parçacığı Durumları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a55409cd2c3bed2bc09db10622de1cceab934112
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45624573"
---
# <a name="managed-thread-states"></a>Yönetilen İş Parçacığı Durumları
Özellik <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> iş parçacığının geçerli durumunu belirten bir bit maskesi sağlar. Bir iş parçacığı her zaman mümkün olan durumlarda en az birinde olan <xref:System.Threading.ThreadState> numaralandırma ve aynı anda birden çok durumda olabilir.  
  
> [!IMPORTANT]
>  İş parçacığı durumu olan birkaç ilgi, yalnızca hata ayıklama senaryoları. Kodunuzu, iş parçacıklarının etkinlikleri eşitlemek için iş parçacığı durumu hiçbir zaman kullanmanız gerekir.  
  
 Yönetilen iş parçacığı oluşturduğunuzda olan <xref:System.Threading.ThreadState.Unstarted> durumu. Kalan iş parçacığı <xref:System.Threading.ThreadState.Unstarted> işletim sistemi tarafından başlatılan duruma gelene kadar belirtin. Çağırma <xref:System.Threading.Thread.Start%2A> bilmeniz işletim sistemi sağlayan iş parçacığı başlatılabilir; iş parçacığı durumunu değiştirmez.  
  
 Yönetilen Ortam girin yönetilmeyen iş parçacığı zaten başlatılmış durumdadır. Bir iş parçacığı başlangıç durumuna geçtiğinde, bir dizi eylem bu durumları değiştirmek neden olabilir. Aşağıdaki tabloda bir değişikliğe karşılık gelen yeni durum birlikte durumunun neden eylemleri listeler.  
  
|Eylem|Ortaya çıkan yeni durum|  
|------------|-------------------------|  
|Oluşturucusu <xref:System.Threading.Thread> sınıfı çağrılır.|<xref:System.Threading.ThreadState.Unstarted>|  
|Başka bir iş parçacığı çağrı <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Unstarted>|  
|Yanıt iş parçacığı <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> ve çalışmaya başlar.|<xref:System.Threading.ThreadState.Running>|  
|İş parçacığı çağrı <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|İş parçacığı çağrı <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> başka bir nesne üzerinde.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|İş parçacığı çağrı <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> başka bir iş parçacığı üzerinde.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Başka bir iş parçacığı çağrı <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.SuspendRequested>|  
|İş parçacığının yanıt veren bir <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> istek.|<xref:System.Threading.ThreadState.Suspended>|  
|Başka bir iş parçacığı çağrı <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Running>|  
|Başka bir iş parçacığı çağrı <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.AbortRequested>|  
|İş parçacığının yanıt veren bir <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Aborted>, ardından <xref:System.Threading.ThreadState.Stopped>|  
  
 Çünkü <xref:System.Threading.ThreadState.Running> durumu 0 değerine sahip, bu durum bulmak için bir bit testi gerçekleştirmek mümkün değildir. Aşağıdaki test (sözde kod) bunun yerine, kullanılabilir:  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 İş parçacıkları genellikle birden fazla belirli bir zamanda durumdadır. Örneğin, bir iş parçacığı üzerinde engellenirse bir <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> çağrısı ve başka bir iş parçacığı çağrı <xref:System.Threading.Thread.Abort%2A> , aynı iş parçacığında hem de iş parçacığı olacaktır <xref:System.Threading.ThreadState.WaitSleepJoin> ve <xref:System.Threading.ThreadState.AbortRequested> aynı anda durumları. Bu durumda, iş parçacığı çağrısından döndürür olarak <xref:System.Threading.Monitor.Wait%2A> veya kesintiye, onu alırsınız <xref:System.Threading.ThreadAbortException>.  
  
 Bir iş parçacığı ayrıldığında <xref:System.Threading.ThreadState.Unstarted> yapılan bir çağrının sonucu durum <xref:System.Threading.Thread.Start%2A>, hiçbir zaman için döndürebilir <xref:System.Threading.ThreadState.Unstarted> durumu. Bir iş parçacığı hiçbir zaman bırakabilirsiniz <xref:System.Threading.ThreadState.Stopped> durumu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.ThreadAbortException>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadState>  
- [İş parçacığı oluşturma](../../../docs/standard/threading/index.md)
