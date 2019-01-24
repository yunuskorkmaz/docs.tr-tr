---
title: Süreölçerler
description: Çok iş parçacıklı bir ortamda kullanmak için hangi .NET zamanlayıcılar hakkında bilgi edinin.
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
ms.author: ronpet
ms.openlocfilehash: 644ccf5951e9d2556fc697d2fd763f026fd0ebdb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617232"
---
# <a name="timers"></a><span data-ttu-id="bbe6d-103">Süreölçerler</span><span class="sxs-lookup"><span data-stu-id="bbe6d-103">Timers</span></span>

<span data-ttu-id="bbe6d-104">.NET, çok iş parçacıklı bir ortamda kullanmak için iki zamanlayıcılar sağlar:</span><span class="sxs-lookup"><span data-stu-id="bbe6d-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="bbe6d-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, üzerinde tek bir geri çağırma yöntemini yürütür bir <xref:System.Threading.ThreadPool> düzenli aralıklarla iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="bbe6d-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, varsayılan olarak yükselten bir olay hakkında bir <xref:System.Threading.ThreadPool> düzenli aralıklarla iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="bbe6d-107">Bazı .NET uygulamalarında ek zamanlayıcılar şunları içerebilir:</span><span class="sxs-lookup"><span data-stu-id="bbe6d-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="bbe6d-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: bir Windows Forms bileşeni düzenli aralıklarla bir olayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="bbe6d-109">Bileşen herhangi bir kullanıcı arabirimi olan ve tek iş parçacıklı bir ortamda kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="bbe6d-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: düzenli aralıkla web sayfası zaman uyumlu veya zaman uyumsuz Geri göndermeler gerçekleştiren bir ASP.NET bileşeni.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="bbe6d-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: tümleştirilmiş bir zamanlayıcı <xref:System.Windows.Threading.Dispatcher> işlenen belirtilen bir zaman aralığı ve belirtilen bir öncelik sırası.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="bbe6d-112">Süre System.Threading.Timer sınıfı</span><span class="sxs-lookup"><span data-stu-id="bbe6d-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="bbe6d-113"><xref:System.Threading.Timer?displayProperty=nameWithType> Sınıfı temsilci belirtilen aralıklarla sürekli olarak çağırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="bbe6d-114">Bu sınıf, belirtilen zaman aralığı içinde bir temsilci tek bir çağrı zamanlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-114">You also can use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="bbe6d-115">Temsilci üzerinde yürütülen bir <xref:System.Threading.ThreadPool> iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="bbe6d-116">Oluştururken bir <xref:System.Threading.Timer?displayProperty=nameWithType> nesne, belirttiğiniz bir <xref:System.Threading.TimerCallback> geri çağırma yöntemi tanımlayan bir temsilci, geri çağırma ve zaman aralığını ilk çağrısıysa önce gecikme süresini geri çağırma geçirilen bir isteğe bağlı durum nesnesi geri çağırmaları arasında.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="bbe6d-117">Bekleyen bir zamanlayıcı iptal etmek için çağrı <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="bbe6d-118">Aşağıdaki örnek, bir saniye (1000 milisaniye cinsinden) sonra ilk kez sağlanan temsilci çağırır ve ardından her iki saniye çağıran bir zamanlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="bbe6d-119">Örnekte durum nesnesi, bir temsilci çağrılır kaç kez saymak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="bbe6d-120">En az 10 kez temsilci çağrıldığında Zamanlayıcı durduruldu.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="bbe6d-121">Daha fazla bilgi ve örnekler için bkz. <xref:System.Threading.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="bbe6d-122">System.Timers.Timer sınıfı</span><span class="sxs-lookup"><span data-stu-id="bbe6d-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="bbe6d-123">Çok iş parçacıklı bir ortamda kullanılabilen başka bir süre ölçer <xref:System.Timers.Timer?displayProperty=nameWithType> varsayılan olarak oluşturan bir olay hakkında bir <xref:System.Threading.ThreadPool> iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="bbe6d-124">Oluştururken bir <xref:System.Timers.Timer?displayProperty=nameWithType> nesnesi, yükseltmek istediğiniz zaman aralığını belirtin bir <xref:System.Timers.Timer.Elapsed> olay.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="bbe6d-125">Kullanım <xref:System.Timers.Timer.Enabled%2A> Zamanlayıcı oluşturması gerektiğini belirtmek için özelliği bir <xref:System.Timers.Timer.Elapsed> olay.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="bbe6d-126">Gerekirse bir <xref:System.Timers.Timer.Elapsed> belirtilen zaman aralığı geçtikten sonra yalnızca bir kez tetiklenecek olayı <xref:System.Timers.Timer.AutoReset%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="bbe6d-127">Varsayılan değer olan <xref:System.Timers.Timer.AutoReset%2A> özelliği `true`, anlamına gelecek şekilde, bir <xref:System.Timers.Timer.Elapsed> olayı oluşturulur düzenli olarak tarafından tanımlanan aralıkta <xref:System.Timers.Timer.Interval%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="bbe6d-128">Daha fazla bilgi ve örnekler için bkz. <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bbe6d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbe6d-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="bbe6d-130">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="bbe6d-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
