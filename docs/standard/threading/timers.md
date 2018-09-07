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
ms.openlocfilehash: 63f9b759621689c129fc356fe38d7e7c5ee41f30
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084526"
---
# <a name="timers"></a><span data-ttu-id="55e57-103">Süreölçerler</span><span class="sxs-lookup"><span data-stu-id="55e57-103">Timers</span></span>

<span data-ttu-id="55e57-104">.NET, çok iş parçacıklı bir ortamda kullanmak için iki zamanlayıcılar sağlar:</span><span class="sxs-lookup"><span data-stu-id="55e57-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="55e57-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, üzerinde tek bir geri çağırma yöntemini yürütür bir <xref:System.Threading.ThreadPool> düzenli aralıklarla iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="55e57-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="55e57-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, varsayılan olarak yükselten bir olay hakkında bir <xref:System.Threading.ThreadPool> düzenli aralıklarla iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="55e57-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="55e57-107">Bazı .NET uygulamalarında ek zamanlayıcılar şunları içerebilir:</span><span class="sxs-lookup"><span data-stu-id="55e57-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="55e57-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: bir Windows Forms bileşeni düzenli aralıklarla bir olayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="55e57-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="55e57-109">Bileşen herhangi bir kullanıcı arabirimi olan ve tek iş parçacıklı bir ortamda kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="55e57-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="55e57-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: düzenli aralıkla web sayfası zaman uyumlu veya zaman uyumsuz Geri göndermeler gerçekleştiren bir ASP.NET bileşeni.</span><span class="sxs-lookup"><span data-stu-id="55e57-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="55e57-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: tümleştirilmiş bir zamanlayıcı <xref:System.Windows.Threading.Dispatcher> işlenen belirtilen bir zaman aralığı ve belirtilen bir öncelik sırası.</span><span class="sxs-lookup"><span data-stu-id="55e57-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="55e57-112">Süre System.Threading.Timer sınıfı</span><span class="sxs-lookup"><span data-stu-id="55e57-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="55e57-113"><xref:System.Threading.Timer?displayProperty=nameWithType> Sınıfı temsilci belirtilen aralıklarla sürekli olarak çağırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="55e57-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="55e57-114">Bu sınıf, belirtilen zaman aralığı içinde bir temsilci tek bir çağrı zamanlamak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="55e57-114">You also can use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="55e57-115">Temsilci üzerinde yürütülen bir <xref:System.Threading.ThreadPool> iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="55e57-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="55e57-116">Oluştururken bir <xref:System.Threading.Timer?displayProperty=nameWithType> nesne, belirttiğiniz bir <xref:System.Threading.TimerCallback> geri çağırma yöntemi tanımlayan bir temsilci, geri çağırma ve zaman aralığını ilk çağrısıysa önce gecikme süresini geri çağırma geçirilen bir isteğe bağlı durum nesnesi geri çağırmaları arasında.</span><span class="sxs-lookup"><span data-stu-id="55e57-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="55e57-117">Bekleyen bir zamanlayıcı iptal etmek için çağrı <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="55e57-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="55e57-118">Aşağıdaki örnek, bir saniye (1000 milisaniye cinsinden) sonra ilk kez sağlanan temsilci çağırır ve ardından her iki saniye çağıran bir zamanlayıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="55e57-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="55e57-119">Örnekte durum nesnesi, bir temsilci çağrılır kaç kez saymak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="55e57-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="55e57-120">En az 10 kez temsilci çağrıldığında Zamanlayıcı durduruldu.</span><span class="sxs-lookup"><span data-stu-id="55e57-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="55e57-121">Daha fazla bilgi ve örnekler için bkz. <xref:System.Threading.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="55e57-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="55e57-122">System.Timers.Timer sınıfı</span><span class="sxs-lookup"><span data-stu-id="55e57-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="55e57-123">Çok iş parçacıklı bir ortamda kullanılabilen başka bir süre ölçer <xref:System.Timers.Timer?displayProperty=nameWithType> varsayılan olarak oluşturan bir olay hakkında bir <xref:System.Threading.ThreadPool> iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="55e57-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="55e57-124">Oluştururken bir <xref:System.Timers.Timer?displayProperty=nameWithType> nesnesi, yükseltmek istediğiniz zaman aralığını belirtin bir <xref:System.Timers.Timer.Elapsed> olay.</span><span class="sxs-lookup"><span data-stu-id="55e57-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="55e57-125">Kullanım <xref:System.Timers.Timer.Enabled%2A> Zamanlayıcı oluşturması gerektiğini belirtmek için özelliği bir <xref:System.Timers.Timer.Elapsed> olay.</span><span class="sxs-lookup"><span data-stu-id="55e57-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="55e57-126">Gerekirse bir <xref:System.Timers.Timer.Elapsed> belirtilen zaman aralığı geçtikten sonra yalnızca bir kez tetiklenecek olayı <xref:System.Timers.Timer.AutoReset%2A> için `false`.</span><span class="sxs-lookup"><span data-stu-id="55e57-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="55e57-127">Varsayılan değer olan <xref:System.Timers.Timer.AutoReset%2A> özelliği `true`, anlamına gelecek şekilde, bir <xref:System.Timers.Timer.Elapsed> olayı oluşturulur düzenli olarak tarafından tanımlanan aralıkta <xref:System.Timers.Timer.Interval%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="55e57-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="55e57-128">Daha fazla bilgi ve örnekler için bkz. <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="55e57-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="55e57-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55e57-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>  
- <xref:System.Timers.Timer?displayProperty=nameWithType>  
- [<span data-ttu-id="55e57-130">İş Parçacığı Nesneleri ve Özellikleri</span><span class="sxs-lookup"><span data-stu-id="55e57-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
