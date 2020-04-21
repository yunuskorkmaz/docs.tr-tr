---
title: Zamanlayıcılar
description: .NET zamanlayıcıların çok iş parçacığı ortamında ne kullanacağını öğrenin.
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
ms.openlocfilehash: d463eb2a8d598dc5ba9b2fb51a6fc08c563e6fe4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739494"
---
# <a name="timers"></a><span data-ttu-id="a5f9e-103">Zamanlayıcılar</span><span class="sxs-lookup"><span data-stu-id="a5f9e-103">Timers</span></span>

<span data-ttu-id="a5f9e-104">.NET, çok iş parçacığı bir ortamda kullanmak üzere iki zamanlayıcı sağlar:</span><span class="sxs-lookup"><span data-stu-id="a5f9e-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="a5f9e-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, düzenli aralıklarla bir iş <xref:System.Threading.ThreadPool> parçacığı üzerinde tek bir geri arama yöntemi yürütür.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="a5f9e-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, varsayılan olarak düzenli aralıklarla bir <xref:System.Threading.ThreadPool> iş parçacığı üzerinde bir olay yükseltir.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="a5f9e-107">Bazı .NET uygulamaları ek zamanlayıcılar içerebilir:</span><span class="sxs-lookup"><span data-stu-id="a5f9e-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="a5f9e-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: bir olayı düzenli aralıklarla ateşleyen bir Windows Forms bileşeni.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="a5f9e-109">Bileşenin kullanıcı arabirimi yoktur ve tek iş parçacığı ortamında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="a5f9e-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: düzenli aralıklarla eşzamanlı veya senkron web sayfası postback'leri gerçekleştiren ASP.NET bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="a5f9e-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: <xref:System.Windows.Threading.Dispatcher> belirli bir zaman aralığında ve belirli bir öncelikte işlenen sıraya entegre edilmiş bir zamanlayıcı.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="a5f9e-112">System.Threading.Timer sınıfı</span><span class="sxs-lookup"><span data-stu-id="a5f9e-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="a5f9e-113">Sınıf, <xref:System.Threading.Timer?displayProperty=nameWithType> belirli zaman aralıklarında sürekli olarak temsilci çağırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="a5f9e-114">Bu sınıfı, belirli bir zaman aralığında bir temsilciye tek bir çağrı zamanlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-114">You can also use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="a5f9e-115">Temsilci bir <xref:System.Threading.ThreadPool> iş parçacığı üzerinde yürütülür.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="a5f9e-116">Bir <xref:System.Threading.Timer?displayProperty=nameWithType> nesne oluşturduğunuzda, <xref:System.Threading.TimerCallback> geri arama yöntemini, geri arama için geçirilen isteğe bağlı durum nesnesini, geri aramanın ilk çağrılmadan önce geciktirilmesi gereken süreyi ve geri arama çağrıları arasındaki zaman aralığını tanımlayan bir temsilci belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="a5f9e-117">Bekleyen bir zamanlayıcıyı iptal <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> etmek için yöntemi arayın.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="a5f9e-118">Aşağıdaki örnek, sağlanan temsilciyi bir saniyeden (1000 milisaniye) sonra ilk kez çağıran ve ardından her iki saniyede bir çağıran bir zamanlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="a5f9e-119">Örnekteki durum nesnesi, temsilcinin kaç kez çağrıldığını saymak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="a5f9e-120">Temsilci en az 10 kez çağrıldığında zamanlayıcı durdurulur.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="a5f9e-121">Daha fazla bilgi ve <xref:System.Threading.Timer?displayProperty=nameWithType>örnekler için bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="a5f9e-122">System.Timers.Timer sınıfı</span><span class="sxs-lookup"><span data-stu-id="a5f9e-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="a5f9e-123">Çok iş parçacığı ortamında kullanılabilecek başka bir <xref:System.Timers.Timer?displayProperty=nameWithType> zamanlayıcı, varsayılan olarak <xref:System.Threading.ThreadPool> bir iş parçacığı üzerinde bir olay yükseltir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="a5f9e-124">Bir <xref:System.Timers.Timer?displayProperty=nameWithType> nesne oluşturduğunuzda, bir <xref:System.Timers.Timer.Elapsed> olayı yükseltmek için zaman aralığını belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="a5f9e-125">Bir <xref:System.Timers.Timer.Enabled%2A> zamanlayıcının bir <xref:System.Timers.Timer.Elapsed> olayı yükseltmesi gerekip gerekmediğini belirtmek için özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="a5f9e-126">Belirtilen aralık <xref:System.Timers.Timer.Elapsed> geçtikten sonra yalnızca bir kez yükseltilecek bir olay <xref:System.Timers.Timer.AutoReset%2A> `false`gerekiyorsa, 'yi ' ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="a5f9e-127"><xref:System.Timers.Timer.AutoReset%2A> Özelliğin varsayılan `true`değeri, bir <xref:System.Timers.Timer.Elapsed> olayın <xref:System.Timers.Timer.Interval%2A> özellik tarafından tanımlanan aralıkta düzenli olarak yükseltildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="a5f9e-128">Daha fazla bilgi ve <xref:System.Timers.Timer?displayProperty=nameWithType>örnekler için bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a5f9e-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5f9e-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="a5f9e-130">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="a5f9e-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
