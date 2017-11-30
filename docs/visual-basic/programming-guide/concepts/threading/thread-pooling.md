---
title: "İş parçacığı havuzu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4903fb7a-eaad-435a-9add-1d1b32de3b83
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33b89d261aa2d038926f8c7e1832436b0cd34019
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="thread-pooling-visual-basic"></a><span data-ttu-id="06714-102">İş parçacığı havuzu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06714-102">Thread Pooling (Visual Basic)</span></span>
<span data-ttu-id="06714-103">A *iş parçacığı havuzu* arka planda çeşitli görevleri gerçekleştirmek için kullanılan iş parçacıklarını koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="06714-103">A *thread pool* is a collection of threads that can be used to perform several tasks in the background.</span></span> <span data-ttu-id="06714-104">(Bkz [parçacıkları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) arka plan bilgileri için.) Bu, birincil iş parçacığı diğer görevleri zaman uyumsuz olarak serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="06714-104">(See [Threading (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/index.md) for background information.) This leaves the primary thread free to perform other tasks asynchronously.</span></span>  
  
 <span data-ttu-id="06714-105">İş parçacığı havuzları genellikle sunucu uygulamalarında görevli olduğu.</span><span class="sxs-lookup"><span data-stu-id="06714-105">Thread pools are often employed in server applications.</span></span> <span data-ttu-id="06714-106">Böylece istek zaman uyumsuz olarak birincil iş parçacığını bağlamadan veya izleyen istekleri işlemeyi geciktirme işlenebilen her gelen istek bir iş parçacığı için iş parçacığı havuzundan atanır.</span><span class="sxs-lookup"><span data-stu-id="06714-106">Each incoming request is assigned to a thread from the thread pool, so that the request can be processed asynchronously, without tying up the primary thread or delaying the processing of subsequent requests.</span></span>  
  
 <span data-ttu-id="06714-107">Bir iş parçacığı havuzu, kendi görev tamamlandığında, bekleyen iş parçacıklarının kuyruğuna burada kullanılabilme döndürülür.</span><span class="sxs-lookup"><span data-stu-id="06714-107">Once a thread in the pool completes its task, it is returned to a queue of waiting threads, where it can be reused.</span></span> <span data-ttu-id="06714-108">Bu yeniden her görev için yeni bir iş parçacığı oluşturma maliyetini önlemek uygulamaları etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="06714-108">This reuse enables applications to avoid the cost of creating a new thread for each task.</span></span>  
  
 <span data-ttu-id="06714-109">İş parçacığı havuzları genellikle iş parçacığı sayısı üst sahiptir.</span><span class="sxs-lookup"><span data-stu-id="06714-109">Thread pools typically have a maximum number of threads.</span></span> <span data-ttu-id="06714-110">Tüm iş parçacıkları meşgul ise, iş parçacıkları kullanılabilir duruma geldiğinde bunların hizmet verilebilir kadar ek görevler sıraya konur.</span><span class="sxs-lookup"><span data-stu-id="06714-110">If all the threads are busy, additional tasks are put in queue until they can be serviced as threads become available.</span></span>  
  
 <span data-ttu-id="06714-111">Kendi iş parçacığı havuzu uygulayabilirsiniz, ancak .NET Framework tarafından sunulan iş parçacığı havuzu kullanma daha kolaydır <xref:System.Threading.ThreadPool> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="06714-111">You can implement your own thread pool, but it is easier to use the thread pool provided by the .NET Framework through the <xref:System.Threading.ThreadPool> class.</span></span>  
  
 <span data-ttu-id="06714-112">İş parçacığı havuzu ile çağrı <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> çalıştırmak istediğiniz bir temsilci yöntemiyle bir yordam ve Visual Basic iş parçacığı oluşturan ve yordamınız çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="06714-112">With thread pooling, you call the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> method with a delegate for the procedure you want to run, and Visual Basic creates the thread and runs your procedure.</span></span>  
  
## <a name="thread-pooling-example"></a><span data-ttu-id="06714-113">İş parçacığı havuzu örnek</span><span class="sxs-lookup"><span data-stu-id="06714-113">Thread Pooling Example</span></span>  
 <span data-ttu-id="06714-114">Aşağıdaki örnek, iş parçacığı çeşitli görevleri başlatmak için havuzu nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="06714-114">The following example shows how you can use thread pooling to start several tasks.</span></span>  
  
```vb  
Public Sub DoWork()  
    ' Queue a task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf SomeLongTask))  
    ' Queue another task.  
    System.Threading.ThreadPool.QueueUserWorkItem(  
        New System.Threading.WaitCallback(AddressOf AnotherLongTask))  
End Sub  
Private Sub SomeLongTask(ByVal state As Object)  
    ' Insert code to perform a long task.  
End Sub  
Private Sub AnotherLongTask(ByVal state As Object)  
    ' Insert code to perform another long task.  
End Sub  
```  
  
 <span data-ttu-id="06714-115">İş parçacığı havuzu bir avantajı, bağımsız değişkenler görev yordama durumu nesnesinde geçirebilirsiniz olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="06714-115">One advantage of thread pooling is that you can pass arguments in a state object to the task procedure.</span></span> <span data-ttu-id="06714-116">Çağırdığınız yordamı birden fazla bağımsız değişken gerektiriyorsa, bir yapının ya da sınıfının bir örneği çevirebilirsiniz bir `Object` veri türü.</span><span class="sxs-lookup"><span data-stu-id="06714-116">If the procedure you are calling requires more than one argument, you can cast a structure or an instance of a class into an `Object` data type.</span></span>  
  
## <a name="thread-pool-parameters-and-return-values"></a><span data-ttu-id="06714-117">İş parçacığı havuzu parametreler ve dönüş değerleri</span><span class="sxs-lookup"><span data-stu-id="06714-117">Thread Pool Parameters and Return Values</span></span>  
 <span data-ttu-id="06714-118">Bir iş parçacığı havuzu iş parçacığından değerler döndüren basit değildir.</span><span class="sxs-lookup"><span data-stu-id="06714-118">Returning values from a thread-pool thread is not straightforward.</span></span> <span data-ttu-id="06714-119">Değerler döndüren bir işlev çağrısında standart yolu için izin verilmiyor `Sub` yordamlar yalnızca tür iş parçacığı havuzu için sıraya yordamı içindir.</span><span class="sxs-lookup"><span data-stu-id="06714-119">The standard way of returning values from a function call is not allowed because `Sub` procedures are the only type of procedure that can be queued to a thread pool.</span></span> <span data-ttu-id="06714-120">Tek yönlü, parametreleri sağlamak ve değerleri olan parametreleri, dönüş değerleri kaydırma tarafından ve yöntemleri bir sarmalayıcı sınıfı açıklandığı gibi dönmek [parametreler ve dönüş değerleri birden çok iş parçacıklı yordamlar (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="06714-120">One way you can provide parameters and return values is by wrapping the parameters, return values, and methods in a wrapper class as described in [Parameters and Return Values for Multithreaded Procedures (Visual Basic)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md).</span></span>  
  
 <span data-ttu-id="06714-121">İsteğe bağlı kullanarak parametreleri sağlamak ve dönüş değerleri için bir easer yoludur `ByVal` durumu nesne değişkeninin <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="06714-121">An easer way to provide parameters and return values is by using the optional `ByVal` state object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="06714-122">Bir sınıfın bir örneğine başvuru geçirmek için bu değişkeni kullanın, örnek üyeleri iş parçacığı havuzu iş parçacığı tarafından değiştirilebilir ve dönüş değerleri olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="06714-122">If you use this variable to pass a reference to an instance of a class, the members of the instance can be modified by the thread-pool thread and used as return values.</span></span>  
  
 <span data-ttu-id="06714-123">İlk bakışta değeri tarafından geçirilen bir değişkeni tarafından başvurulan nesne değiştirebileceğiniz belirgin olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="06714-123">At first it may not be obvious that you can modify an object referred to by a variable that is passed by value.</span></span> <span data-ttu-id="06714-124">Yalnızca nesne başvurusu değeriyle geçtiğinden bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06714-124">You can do this because only the object reference is passed by value.</span></span> <span data-ttu-id="06714-125">Nesne başvurusu tarafından başvurulan nesne üyeleri değişiklik yaptığınızda, değişiklikler gerçek sınıf örneğine uygulanır.</span><span class="sxs-lookup"><span data-stu-id="06714-125">When you make changes to members of the object referred to by the object reference, the changes apply to the actual class instance.</span></span>  
  
 <span data-ttu-id="06714-126">Yapılar, durum nesneleri içinde değer döndürmek için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="06714-126">Structures cannot be used to return values inside state objects.</span></span> <span data-ttu-id="06714-127">Zaman uyumsuz işlem yaptığı değişiklikler yapıları değer türleri olduğundan, özgün yapısı üyeleri değiştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="06714-127">Because structures are value types, changes that the asynchronous process makes do not change the members of the original structure.</span></span> <span data-ttu-id="06714-128">Dönüş değerleri değil gerektiğinde parametreleri sağlamak amacıyla yapıları kullanın.</span><span class="sxs-lookup"><span data-stu-id="06714-128">Use structures to provide parameters when return values are not needed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06714-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="06714-129">See Also</span></span>  
 <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [<span data-ttu-id="06714-130">Nasıl yapılır: iş parçacığı havuzu (Visual Basic) kullanma</span><span class="sxs-lookup"><span data-stu-id="06714-130">How to: Use a Thread Pool (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/how-to-use-a-thread-pool.md)  
 [<span data-ttu-id="06714-131">İş parçacığı oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06714-131">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="06714-132">Birden çok iş parçacıklı uygulamalar (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06714-132">Multithreaded Applications (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/multithreaded-applications.md)  
 [<span data-ttu-id="06714-133">İş parçacığı eşitleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06714-133">Thread Synchronization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)
