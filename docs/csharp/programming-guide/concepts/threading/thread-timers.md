---
title: "İş parçacığı zamanlayıcılar (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 52ed71e8-4fd9-43a4-ae40-04cce7cff23f
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9702360408340b28fcdcc8f197467a002f77ee51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="thread-timers-c"></a><span data-ttu-id="ac7b1-102">İş parçacığı zamanlayıcılar (C#)</span><span class="sxs-lookup"><span data-stu-id="ac7b1-102">Thread Timers (C#)</span></span>
<span data-ttu-id="ac7b1-103"><xref:System.Threading.Timer?displayProperty=nameWithType> Sınıfı, bir görev ayrı bir iş parçacığı üzerinde düzenli olarak çalıştırmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-103">The <xref:System.Threading.Timer?displayProperty=nameWithType> class is useful for periodically running a task on a separate thread.</span></span> <span data-ttu-id="ac7b1-104">Örneğin, bir iş parçacığı süreölçer durumunu ve bir veritabanının bütünlüğünü denetlemek için veya kritik dosyalarını yedeklemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-104">For example, you could use a thread timer to check the status and integrity of a database or to back up critical files.</span></span>  
  
## <a name="thread-timer-example"></a><span data-ttu-id="ac7b1-105">İş parçacığı Zamanlayıcı örneği</span><span class="sxs-lookup"><span data-stu-id="ac7b1-105">Thread Timer Example</span></span>  
 <span data-ttu-id="ac7b1-106">Aşağıdaki örnek, her iki saniyede bir görev başlatır ve başlatmak için bir bayrak kullanır <xref:System.IDisposable.Dispose%2A> Zamanlayıcı durdurur yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-106">The following example starts a task every two seconds and uses a flag to initiate the <xref:System.IDisposable.Dispose%2A> method that stops the timer.</span></span> <span data-ttu-id="ac7b1-107">Bu örnek çıktı penceresine durum gönderir.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-107">This example posts status to the output window.</span></span>  
  
```csharp  
private class StateObjClass  
{  
    // Used to hold parameters for calls to TimerTask.  
    public int SomeValue;  
    public System.Threading.Timer TimerReference;  
    public bool TimerCanceled;  
}  
  
public void RunTimer()  
{  
    StateObjClass StateObj = new StateObjClass();  
    StateObj.TimerCanceled = false;  
    StateObj.SomeValue = 1;  
    System.Threading.TimerCallback TimerDelegate =  
        new System.Threading.TimerCallback(TimerTask);  
  
    // Create a timer that calls a procedure every 2 seconds.  
    // Note: There is no Start method; the timer starts running as soon as   
    // the instance is created.  
    System.Threading.Timer TimerItem =  
        new System.Threading.Timer(TimerDelegate, StateObj, 2000, 2000);  
  
    // Save a reference for Dispose.  
    StateObj.TimerReference = TimerItem;    
  
    // Run for ten loops.  
    while (StateObj.SomeValue < 10)   
    {  
        // Wait one second.  
        System.Threading.Thread.Sleep(1000);    
    }  
  
    // Request Dispose of the timer object.  
    StateObj.TimerCanceled = true;    
}  
  
private void TimerTask(object StateObj)  
{  
    StateObjClass State = (StateObjClass)StateObj;  
    // Use the interlocked class to increment the counter variable.  
    System.Threading.Interlocked.Increment(ref State.SomeValue);  
    System.Diagnostics.Debug.WriteLine("Launched new thread  " + DateTime.Now.ToString());  
    if (State.TimerCanceled)      
    // Dispose Requested.  
    {  
        State.TimerReference.Dispose();  
        System.Diagnostics.Debug.WriteLine("Done  " + DateTime.Now.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="ac7b1-108">İş parçacığı zamanlayıcıları özellikle yararlı ne zaman <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> nesnesidir konsol uygulamaları zaman geliştirdiğiniz gibi kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-108">Thread timers are particularly useful when the <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> object is unavailable, such as when you are developing console applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac7b1-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac7b1-109">See Also</span></span>  
 <xref:System.Threading>  
 [<span data-ttu-id="ac7b1-110">Birden çok iş parçacıklı uygulamalar (C#)</span><span class="sxs-lookup"><span data-stu-id="ac7b1-110">Multithreaded Applications (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)
