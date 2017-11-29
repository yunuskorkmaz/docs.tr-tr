---
title: "Nasıl yapılır: iş parçacığı havuzu (C#) kullanma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 210a9235-83a6-420b-af52-2d6a58e5133f
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ad5ffb224821c67d227297f8a5a4a1476d77b0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-thread-pool-c"></a>Nasıl yapılır: iş parçacığı havuzu (C#) kullanma
*İş parçacığı havuzu* biçimidir hangi görevleri bir kuyruğuna eklendi ve iş parçacıkları oluşturulduğunda otomatik olarak başlatılan çoklu iş parçacığı kullanımı. Daha fazla bilgi için bkz: [iş parçacığı havuzu (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md).  
  
 Aşağıdaki örnek, hesaplamak için .NET Framework iş parçacığı havuzu kullanır `Fibonacci` rakamdan 20 ile 40 arasında sonucu. Her `Fibonacci` sonucu ile temsil edilir `Fibonacci` adlı bir yöntem sağlar sınıfı `ThreadPoolCallback` hesaplama gerçekleştirir. Her temsil eden bir nesne `Fibonacci` değer oluşturulur ve `ThreadPoolCallback` yöntemi iletilir <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, yöntemin havuzunda kullanılabilir bir iş parçacığı atar.  
  
 Çünkü her `Fibonacci` nesne işlem yarı rastgele bir değeri verilir ve her iş parçacığı için işlemci zamanının rekabet çünkü önceden ne kadar hesaplanacak on için tüm sonuçları sürer bilemezsiniz. İşte bu nedenle her `Fibonacci` nesne örneği geçirilen <xref:System.Threading.ManualResetEvent> oluşturma sırasında sınıfı. Her nesne sağlanan olay nesnesi sinyalleri kendi hesaplama tamamlandığında, blok yürütme ile birincil iş parçacığına sağlayan <xref:System.Threading.WaitHandle.WaitAll%2A> on kadar `Fibonacci` nesneleri bir sonuç hesaplanan. `Main` Yöntemi ardından görüntüler her `Fibonacci` sonucu.  
  
## <a name="example"></a>Örnek  
  
```csharp  
using System;  
using System.Threading;  
  
public class Fibonacci  
{  
    private int _n;  
    private int _fibOfN;  
    private ManualResetEvent _doneEvent;  
  
    public int N { get { return _n; } }  
    public int FibOfN { get { return _fibOfN; } }  
  
    // Constructor.  
    public Fibonacci(int n, ManualResetEvent doneEvent)  
    {  
        _n = n;  
        _doneEvent = doneEvent;  
    }  
  
    // Wrapper method for use with thread pool.  
    public void ThreadPoolCallback(Object threadContext)  
    {  
        int threadIndex = (int)threadContext;  
        Console.WriteLine("thread {0} started...", threadIndex);  
        _fibOfN = Calculate(_n);  
        Console.WriteLine("thread {0} result calculated...", threadIndex);  
        _doneEvent.Set();  
    }  
  
    // Recursive method that calculates the Nth Fibonacci number.  
    public int Calculate(int n)  
    {  
        if (n <= 1)  
        {  
            return n;  
        }  
  
        return Calculate(n - 1) + Calculate(n - 2);  
    }  
}  
  
public class ThreadPoolExample  
{  
    static void Main()  
    {  
        const int FibonacciCalculations = 10;  
  
        // One event is used for each Fibonacci object.  
        ManualResetEvent[] doneEvents = new ManualResetEvent[FibonacciCalculations];  
        Fibonacci[] fibArray = new Fibonacci[FibonacciCalculations];  
        Random r = new Random();  
  
        // Configure and start threads using ThreadPool.  
        Console.WriteLine("launching {0} tasks...", FibonacciCalculations);  
        for (int i = 0; i < FibonacciCalculations; i++)  
        {  
            doneEvents[i] = new ManualResetEvent(false);  
            Fibonacci f = new Fibonacci(r.Next(20, 40), doneEvents[i]);  
            fibArray[i] = f;  
            ThreadPool.QueueUserWorkItem(f.ThreadPoolCallback, i);  
        }  
  
        // Wait for all threads in pool to calculate.  
        WaitHandle.WaitAll(doneEvents);  
        Console.WriteLine("All calculations are complete.");  
  
        // Display the results.  
        for (int i= 0; i<FibonacciCalculations; i++)  
        {  
            Fibonacci f = fibArray[i];  
            Console.WriteLine("Fibonacci({0}) = {1}", f.N, f.FibOfN);  
        }  
    }  
}  
```  
  
 Aşağıdaki çıkış örneğidir.  
  
```  
launching 10 tasks...  
thread 0 started...  
thread 1 started...  
thread 1 result calculated...  
thread 2 started...  
thread 2 result calculated...  
thread 3 started...  
thread 3 result calculated...  
thread 4 started...  
thread 0 result calculated...  
thread 5 started...  
thread 5 result calculated...  
thread 6 started...  
thread 4 result calculated...  
thread 7 started...  
thread 6 result calculated...  
thread 8 started...  
thread 8 result calculated...  
thread 9 started...  
thread 9 result calculated...  
thread 7 result calculated...  
All calculations are complete.  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(25) = 75025  
Fibonacci(22) = 17711  
Fibonacci(38) = 39088169  
Fibonacci(29) = 514229  
Fibonacci(29) = 514229  
Fibonacci(38) = 39088169  
Fibonacci(21) = 10946  
Fibonacci(27) = 196418  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [İş parçacığı havuzu (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [İş parçacığı (C#)](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [Güvenlik](../../../../standard/security/index.md)
