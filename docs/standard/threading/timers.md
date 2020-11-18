---
title: Zamanlayıcılar
description: Çok iş parçacıklı bir ortamda kullanılacak .NET zamanlayıcıları hakkında bilgi edinin.
ms.date: 07/03/2018
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.openlocfilehash: 1ab612bc32a84c1248d311b0603a01a32a25199f
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826111"
---
# <a name="timers"></a><span data-ttu-id="bc057-103">Zamanlayıcılar</span><span class="sxs-lookup"><span data-stu-id="bc057-103">Timers</span></span>

<span data-ttu-id="bc057-104">.NET, çok iş parçacıklı bir ortamda kullanmak için iki Zamanlayıcı sağlar:</span><span class="sxs-lookup"><span data-stu-id="bc057-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="bc057-105"><xref:System.Threading.Timer?displayProperty=nameWithType>düzenli aralıklarla bir iş parçacığında tek bir geri çağırma yöntemi yürüten <xref:System.Threading.ThreadPool> .</span><span class="sxs-lookup"><span data-stu-id="bc057-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="bc057-106"><xref:System.Timers.Timer?displayProperty=nameWithType>Bu, varsayılan olarak <xref:System.Threading.ThreadPool> düzenli aralıklarla bir iş parçacığında bir olay oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bc057-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="bc057-107">Bazı .NET uygulamaları ek zamanlayıcılar içerebilir:</span><span class="sxs-lookup"><span data-stu-id="bc057-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="bc057-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: düzenli aralıklarla bir olayı harekete uygulayan Windows Forms bileşen.</span><span class="sxs-lookup"><span data-stu-id="bc057-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="bc057-109">Bileşen Kullanıcı arabirimine sahip değildir ve tek iş parçacıklı bir ortamda kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bc057-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="bc057-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: düzenli bir aralıkta zaman uyumsuz veya zaman uyumlu Web sayfası geri gönderileri gerçekleştiren bir ASP.NET bileşeni.</span><span class="sxs-lookup"><span data-stu-id="bc057-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="bc057-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: <xref:System.Windows.Threading.Dispatcher> belirli bir zaman aralığında ve belirtilen öncelikte işlenen kuyrukla tümleştirilmiş bir zamanlayıcı.</span><span class="sxs-lookup"><span data-stu-id="bc057-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="bc057-112">System. Threading. Timer sınıfı</span><span class="sxs-lookup"><span data-stu-id="bc057-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="bc057-113"><xref:System.Threading.Timer?displayProperty=nameWithType>Sınıfı, belirli zaman aralıklarında bir temsilciyi sürekli olarak çağırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc057-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="bc057-114">Bu sınıfı, belirli bir zaman aralığındaki bir temsilciye tek bir çağrı zamanlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc057-114">You can also use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="bc057-115">Temsilci bir <xref:System.Threading.ThreadPool> iş parçacığında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="bc057-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="bc057-116">Bir nesne oluşturduğunuzda, geri <xref:System.Threading.Timer?displayProperty=nameWithType> <xref:System.Threading.TimerCallback> çağırma yöntemini, geri çağrıya geçirilen isteğe bağlı bir durum nesnesini, geri aramanın ilk çağrısından önce gecikme süresini ve geri çağırma çağırmaları arasındaki zaman aralığını tanımlayan bir temsilci belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc057-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="bc057-117">Bekleyen bir zamanlayıcıyı iptal etmek için yöntemini çağırın <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="bc057-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="bc057-118">Aşağıdaki örnek, belirtilen temsilciyi bir saniyeden sonra ilk kez çağıran bir zamanlayıcı oluşturur (1000 milisaniye) ve ardından iki saniyede bir çağırır.</span><span class="sxs-lookup"><span data-stu-id="bc057-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="bc057-119">Örnekteki durum nesnesi, temsilcinin kaç kez çağrıldığını saymak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bc057-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="bc057-120">Temsilci, en az 10 kez çağrıldığında Zamanlayıcı durdurulur.</span><span class="sxs-lookup"><span data-stu-id="bc057-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="bc057-121">Daha fazla bilgi ve örnek için bkz <xref:System.Threading.Timer?displayProperty=nameWithType> ..</span><span class="sxs-lookup"><span data-stu-id="bc057-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="bc057-122">System. süreölçerler. Timer sınıfı</span><span class="sxs-lookup"><span data-stu-id="bc057-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="bc057-123">Çoklu iş parçacıklı bir ortamda kullanılabilen bir zamanlayıcı, <xref:System.Timers.Timer?displayProperty=nameWithType> Varsayılan olarak bir iş parçacığında bir olay oluşturur <xref:System.Threading.ThreadPool> .</span><span class="sxs-lookup"><span data-stu-id="bc057-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="bc057-124">Bir <xref:System.Timers.Timer?displayProperty=nameWithType> nesne oluşturduğunuzda, bir olayın tetikkaydedileceği zaman aralığını belirtebilirsiniz <xref:System.Timers.Timer.Elapsed> .</span><span class="sxs-lookup"><span data-stu-id="bc057-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="bc057-125"><xref:System.Timers.Timer.Enabled%2A>Bir zamanlayıcının bir olayı oluşturup tetiklemeyeceğini göstermek için özelliğini kullanın <xref:System.Timers.Timer.Elapsed> .</span><span class="sxs-lookup"><span data-stu-id="bc057-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="bc057-126">Bir <xref:System.Timers.Timer.Elapsed> olayın yalnızca belirtilen Aralık geçtikten sonra bir kez ortaya çıkarılmasının gerekmesi durumunda, öğesini <xref:System.Timers.Timer.AutoReset%2A> olarak ayarlayın `false` .</span><span class="sxs-lookup"><span data-stu-id="bc057-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="bc057-127">Özelliğinin varsayılan değeri, <xref:System.Timers.Timer.AutoReset%2A> `true` bir <xref:System.Timers.Timer.Elapsed> olayın özelliği tarafından tanımlanan aralıkta düzenli olarak oluşturulduğu anlamına gelir <xref:System.Timers.Timer.Interval%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc057-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="bc057-128">Daha fazla bilgi ve örnek için bkz <xref:System.Timers.Timer?displayProperty=nameWithType> ..</span><span class="sxs-lookup"><span data-stu-id="bc057-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bc057-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc057-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="bc057-130">İş parçacığı nesneleri ve özellikleri</span><span class="sxs-lookup"><span data-stu-id="bc057-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
