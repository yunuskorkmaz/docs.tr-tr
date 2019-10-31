---
title: Süreölçerler
description: Çok iş parçacıklı bir ortamda kullanılacak .NET zamanlayıcıları hakkında bilgi edinin.
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.openlocfilehash: d7d1fa13b02fe7425fa9b4cb81ba20297a23fe4b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128945"
---
# <a name="timers"></a><span data-ttu-id="65a5c-103">Süreölçerler</span><span class="sxs-lookup"><span data-stu-id="65a5c-103">Timers</span></span>

<span data-ttu-id="65a5c-104">.NET, çok iş parçacıklı bir ortamda kullanmak için iki Zamanlayıcı sağlar:</span><span class="sxs-lookup"><span data-stu-id="65a5c-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="65a5c-105">düzenli aralıklarla <xref:System.Threading.ThreadPool> iş parçacığında tek bir geri çağırma yöntemi yürüten <xref:System.Threading.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65a5c-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="65a5c-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, varsayılan olarak düzenli aralıklarla bir <xref:System.Threading.ThreadPool> iş parçacığı üzerinde bir olay oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65a5c-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="65a5c-107">Bazı .NET uygulamaları ek zamanlayıcılar içerebilir:</span><span class="sxs-lookup"><span data-stu-id="65a5c-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="65a5c-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: düzenli aralıklarla bir olayı harekete uygulayan Windows Forms bir bileşen.</span><span class="sxs-lookup"><span data-stu-id="65a5c-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="65a5c-109">Bileşen Kullanıcı arabirimine sahip değildir ve tek iş parçacıklı bir ortamda kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="65a5c-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="65a5c-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: düzenli bir aralıkta zaman uyumsuz veya zaman uyumlu Web sayfası geri göndermeler gerçekleştiren bir ASP.NET bileşeni.</span><span class="sxs-lookup"><span data-stu-id="65a5c-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="65a5c-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: belirli bir zaman aralığında ve belirtilen öncelikte işlenen <xref:System.Windows.Threading.Dispatcher> kuyruğu ile tümleştirilmiş bir zamanlayıcı.</span><span class="sxs-lookup"><span data-stu-id="65a5c-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="65a5c-112">System. Threading. Timer sınıfı</span><span class="sxs-lookup"><span data-stu-id="65a5c-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="65a5c-113"><xref:System.Threading.Timer?displayProperty=nameWithType> sınıfı, belirli zaman aralıklarında bir temsilciyi sürekli olarak çağırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="65a5c-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="65a5c-114">Bu sınıfı, belirli bir zaman aralığındaki bir temsilciye tek bir çağrı zamanlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65a5c-114">You also can use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="65a5c-115">Temsilci <xref:System.Threading.ThreadPool> bir iş parçacığında yürütülür.</span><span class="sxs-lookup"><span data-stu-id="65a5c-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="65a5c-116"><xref:System.Threading.Timer?displayProperty=nameWithType> nesnesi oluşturduğunuzda, geri çağırma yöntemini, geri çağrıya geçirilen isteğe bağlı bir durum nesnesini, geri aramanın ilk çağrısından önce gecikme süresini ve arasındaki zaman aralığını tanımlayan bir <xref:System.Threading.TimerCallback> temsilcisi belirtirsiniz. geri çağırma çağırmaları.</span><span class="sxs-lookup"><span data-stu-id="65a5c-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="65a5c-117">Bekleyen bir zamanlayıcıyı iptal etmek için <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="65a5c-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="65a5c-118">Aşağıdaki örnek, belirtilen temsilciyi bir saniyeden sonra ilk kez çağıran bir zamanlayıcı oluşturur (1000 milisaniye) ve ardından iki saniyede bir çağırır.</span><span class="sxs-lookup"><span data-stu-id="65a5c-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="65a5c-119">Örnekteki durum nesnesi, temsilcinin kaç kez çağrıldığını saymak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="65a5c-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="65a5c-120">Temsilci, en az 10 kez çağrıldığında Zamanlayıcı durdurulur.</span><span class="sxs-lookup"><span data-stu-id="65a5c-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="65a5c-121">Daha fazla bilgi ve örnek için bkz. <xref:System.Threading.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65a5c-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="65a5c-122">System. süreölçerler. Timer sınıfı</span><span class="sxs-lookup"><span data-stu-id="65a5c-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="65a5c-123">Çoklu iş parçacıklı bir ortamda kullanılabilen başka bir zamanlayıcı, varsayılan olarak bir <xref:System.Threading.ThreadPool> iş parçacığında bir olay harekete geçirirse <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65a5c-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="65a5c-124">Bir <xref:System.Timers.Timer?displayProperty=nameWithType> nesnesi oluşturduğunuzda, bir <xref:System.Timers.Timer.Elapsed> olayının tetikkaydedileceği zaman aralığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="65a5c-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="65a5c-125">Bir zamanlayıcının bir <xref:System.Timers.Timer.Elapsed> olayı oluşturup yükseltmeyeceğini göstermek için <xref:System.Timers.Timer.Enabled%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="65a5c-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="65a5c-126">Bir <xref:System.Timers.Timer.Elapsed> olayının, belirtilen Aralık geçtikten sonra yalnızca bir kez ortaya çıkarıldıktan sonra, <xref:System.Timers.Timer.AutoReset%2A> `false`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="65a5c-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="65a5c-127"><xref:System.Timers.Timer.AutoReset%2A> özelliğinin varsayılan değeri `true`ve bu, <xref:System.Timers.Timer.Elapsed> bir olayın <xref:System.Timers.Timer.Interval%2A> özelliği tarafından tanımlanan aralıkta düzenli olarak oluşturulduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="65a5c-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="65a5c-128">Daha fazla bilgi ve örnek için bkz. <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="65a5c-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="65a5c-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65a5c-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="65a5c-130">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="65a5c-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
