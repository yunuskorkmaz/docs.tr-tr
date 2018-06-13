---
title: 'Nasıl yapılır: iş parçacığı havuzu (Visual Basic) kullanma'
ms.date: 07/20/2015
ms.assetid: 90a0bb24-39f8-41f5-a217-b52a7d4fed0b
ms.openlocfilehash: a61defc2e40662d7fdadb40693e757fa559adb6a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648157"
---
# <a name="how-to-use-a-thread-pool-visual-basic"></a><span data-ttu-id="70860-102">Nasıl yapılır: iş parçacığı havuzu (Visual Basic) kullanma</span><span class="sxs-lookup"><span data-stu-id="70860-102">How to: Use a Thread Pool (Visual Basic)</span></span>
<span data-ttu-id="70860-103">*İş parçacığı havuzu* biçimidir hangi görevleri bir kuyruğuna eklendi ve iş parçacıkları oluşturulduğunda otomatik olarak başlatılan çoklu iş parçacığı kullanımı.</span><span class="sxs-lookup"><span data-stu-id="70860-103">*Thread pooling* is a form of multithreading in which tasks are added to a queue and automatically started when threads are created.</span></span> <span data-ttu-id="70860-104">Daha fazla bilgi için bkz: [iş parçacığı havuzu (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="70860-104">For more information, see [Thread Pooling (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md).</span></span>  
  
 <span data-ttu-id="70860-105">Aşağıdaki örnek, hesaplamak için .NET Framework iş parçacığı havuzu kullanır `Fibonacci` rakamdan 20 ile 40 arasında sonucu.</span><span class="sxs-lookup"><span data-stu-id="70860-105">The following example uses the .NET Framework thread pool to calculate the `Fibonacci` result for ten numbers between 20 and 40.</span></span> <span data-ttu-id="70860-106">Her `Fibonacci` sonucu ile temsil edilir `Fibonacci` adlı bir yöntem sağlar sınıfı `ThreadPoolCallback` hesaplama gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="70860-106">Each `Fibonacci` result is represented by the `Fibonacci` class, which provides a method named `ThreadPoolCallback` that performs the calculation.</span></span> <span data-ttu-id="70860-107">Her temsil eden bir nesne `Fibonacci` değer oluşturulur ve `ThreadPoolCallback` yöntemi iletilir <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, yöntemin havuzunda kullanılabilir bir iş parçacığı atar.</span><span class="sxs-lookup"><span data-stu-id="70860-107">An object that represents each `Fibonacci` value is created, and the `ThreadPoolCallback` method is passed to <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>, which assigns an available thread in the pool to execute the method.</span></span>  
  
 <span data-ttu-id="70860-108">Çünkü her `Fibonacci` nesne işlem yarı rastgele bir değeri verilir ve her iş parçacığı için işlemci zamanının rekabet çünkü önceden ne kadar hesaplanacak on için tüm sonuçları sürer bilemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="70860-108">Because each `Fibonacci` object is given a semi-random value to compute, and because each thread will be competing for processor time, you cannot know in advance how long it will take for all ten results to be calculated.</span></span> <span data-ttu-id="70860-109">İşte bu nedenle her `Fibonacci` nesne örneği geçirilen <xref:System.Threading.ManualResetEvent> oluşturma sırasında sınıfı.</span><span class="sxs-lookup"><span data-stu-id="70860-109">That is why each `Fibonacci` object is passed an instance of the <xref:System.Threading.ManualResetEvent> class during construction.</span></span> <span data-ttu-id="70860-110">Her nesne sağlanan olay nesnesi sinyalleri kendi hesaplama tamamlandığında, blok yürütme ile birincil iş parçacığına sağlayan <xref:System.Threading.WaitHandle.WaitAll%2A> on kadar `Fibonacci` nesneleri bir sonuç hesaplanan.</span><span class="sxs-lookup"><span data-stu-id="70860-110">Each object signals the provided event object when its calculation is complete, which allows the primary thread to block execution with <xref:System.Threading.WaitHandle.WaitAll%2A> until all ten `Fibonacci` objects have calculated a result.</span></span> <span data-ttu-id="70860-111">`Main` Yöntemi ardından görüntüler her `Fibonacci` sonucu.</span><span class="sxs-lookup"><span data-stu-id="70860-111">The `Main` method then displays each `Fibonacci` result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70860-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="70860-112">Example</span></span>  
  
```vb  
Imports System.Threading  
  
Module Module1  
  
    Public Class Fibonacci  
        Private _n As Integer  
        Private _fibOfN  
        Private _doneEvent As ManualResetEvent  
  
        Public ReadOnly Property N() As Integer  
            Get  
                Return _n  
            End Get  
        End Property  
  
        Public ReadOnly Property FibOfN() As Integer  
            Get  
                Return _fibOfN  
            End Get  
        End Property  
  
        Sub New(ByVal n As Integer, ByVal doneEvent As ManualResetEvent)  
            _n = n  
            _doneEvent = doneEvent  
        End Sub  
  
        ' Wrapper method for use with the thread pool.  
        Public Sub ThreadPoolCallBack(ByVal threadContext As Object)  
            Dim threadIndex As Integer = CType(threadContext, Integer)  
            Console.WriteLine("thread {0} started...", threadIndex)  
            _fibOfN = Calculate(_n)  
            Console.WriteLine("thread {0} result calculated...", threadIndex)  
            _doneEvent.Set()  
        End Sub  
  
        Public Function Calculate(ByVal n As Integer) As Integer  
            If n <= 1 Then  
                Return n  
            End If  
            Return Calculate(n - 1) + Calculate(n - 2)  
        End Function  
  
    End Class  
  
    <MTAThread()>   
    Sub Main()  
        Const FibonacciCalculations As Integer = 9 ' 0 to 9  
  
        ' One event is used for each Fibonacci object  
        Dim doneEvents(FibonacciCalculations) As ManualResetEvent  
        Dim fibArray(FibonacciCalculations) As Fibonacci  
        Dim r As New Random()  
  
        ' Configure and start threads using ThreadPool.  
        Console.WriteLine("launching {0} tasks...", FibonacciCalculations)  
  
        For i As Integer = 0 To FibonacciCalculations  
            doneEvents(i) = New ManualResetEvent(False)  
            Dim f = New Fibonacci(r.Next(20, 40), doneEvents(i))  
            fibArray(i) = f  
            ThreadPool.QueueUserWorkItem(AddressOf f.ThreadPoolCallBack, i)  
        Next  
  
        ' Wait for all threads in pool to calculate.  
        WaitHandle.WaitAll(doneEvents)  
        Console.WriteLine("All calculations are complete.")  
  
        ' Display the results.  
        For i As Integer = 0 To FibonacciCalculations  
            Dim f As Fibonacci = fibArray(i)  
            Console.WriteLine("Fibonacci({0}) = {1}", f.N, f.FibOfN)  
        Next  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="70860-113">Aşağıdaki çıkış örneğidir.</span><span class="sxs-lookup"><span data-stu-id="70860-113">Following is an example of the output.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70860-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70860-114">See Also</span></span>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.ThreadPool>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="70860-115">İş parçacığı havuzu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70860-115">Thread Pooling (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-pooling.md)  
 [<span data-ttu-id="70860-116">İş parçacığı oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70860-116">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="70860-117">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="70860-117">Security</span></span>](../../../../standard/security/index.md)
