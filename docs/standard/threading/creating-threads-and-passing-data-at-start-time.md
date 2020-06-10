---
title: Başlatma zamanında iş parçacığı oluşturma ve veri geçirme
description: .NET 'teki bir işletim sistemi işleminin başlangıç saatinde iş parçacıkları oluşturmayı ve verileri nasıl geçibileceğinizi anlayın.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
ms.openlocfilehash: 811028d3c853441ff3a61d3628a44e5c65ba7059
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661920"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="20396-103">Başlatma zamanında iş parçacığı oluşturma ve veri geçirme</span><span class="sxs-lookup"><span data-stu-id="20396-103">Creating threads and passing data at start time</span></span>

<span data-ttu-id="20396-104">Bir işletim sistemi işlemi oluşturulduğunda, işletim sistemi, özgün uygulama etki alanı dahil olmak üzere, bu işlemdeki kodu yürütmek için bir iş parçacığını çıkartır.</span><span class="sxs-lookup"><span data-stu-id="20396-104">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="20396-105">Bu noktadan itibaren, uygulama etki alanları, herhangi bir işletim sistemi iş parçacığı oluşturulması veya yok olması gerekmeden oluşturulabilir ve yok edilebilir.</span><span class="sxs-lookup"><span data-stu-id="20396-105">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="20396-106">Yürütülen kod yönetilen kodse, <xref:System.Threading.Thread> geçerli uygulama etki alanında yürütülen iş parçacığına ait bir nesne, türünün statik özelliği alınırken elde edilebilir <xref:System.Threading.Thread.CurrentThread%2A> <xref:System.Threading.Thread> .</span><span class="sxs-lookup"><span data-stu-id="20396-106">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="20396-107">Bu konu, iş parçacığı oluşturma işlemini açıklar ve iş parçacığı yordamına veri geçirme alternatiflerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="20396-107">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="20396-108">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="20396-108">Creating a thread</span></span>

 <span data-ttu-id="20396-109">Yeni bir <xref:System.Threading.Thread> nesne oluşturmak yeni bir yönetilen iş parçacığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="20396-109">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="20396-110"><xref:System.Threading.Thread>Sınıf, bir <xref:System.Threading.ThreadStart> temsilci veya temsilci alan oluşturuculara sahiptir <xref:System.Threading.ParameterizedThreadStart> ; temsilci, yöntemini çağırdığınızda yeni iş parçacığı tarafından çağrılan yöntemi sarar <xref:System.Threading.Thread.Start%2A> .</span><span class="sxs-lookup"><span data-stu-id="20396-110">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="20396-111">Birden <xref:System.Threading.Thread.Start%2A> çok kez çağırma bir, oluşturulmasına neden olur <xref:System.Threading.ThreadStateException> .</span><span class="sxs-lookup"><span data-stu-id="20396-111">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="20396-112"><xref:System.Threading.Thread.Start%2A>Yöntemi hemen, genellikle yeni iş parçacığı başlamadan önce döndürülür.</span><span class="sxs-lookup"><span data-stu-id="20396-112">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="20396-113"><xref:System.Threading.Thread.ThreadState%2A> <xref:System.Threading.Thread.IsAlive%2A> İş parçacığının durumunu herhangi bir anda anlamak için ve özelliklerini kullanabilirsiniz, ancak bu özellikler hiçbir zaman iş parçacığı etkinliklerini eşitlemek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="20396-113">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20396-114">Bir iş parçacığı başlatıldıktan sonra, nesnesine bir başvuru tutulması gerekli değildir <xref:System.Threading.Thread> .</span><span class="sxs-lookup"><span data-stu-id="20396-114">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="20396-115">İş parçacığı yordamı sona erene kadar iş parçacığı yürütülmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="20396-115">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="20396-116">Aşağıdaki kod örneği, başka bir nesne üzerinde örnek ve statik yöntemleri çağırmak için iki yeni iş parçacığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="20396-116">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="20396-117">İş parçacıklarına veri geçirme</span><span class="sxs-lookup"><span data-stu-id="20396-117">Passing data to threads</span></span>

 <span data-ttu-id="20396-118">.NET Framework sürüm 2,0 ' de temsilci, <xref:System.Threading.ParameterizedThreadStart> yöntem aşırı yüklemesini çağırdığınızda bir iş parçacığına veri içeren bir nesneyi geçirmek için kolay bir yol sağlar <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="20396-118">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="20396-119"><xref:System.Threading.ParameterizedThreadStart>Kod örneği için bkz..</span><span class="sxs-lookup"><span data-stu-id="20396-119">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="20396-120"><xref:System.Threading.ParameterizedThreadStart> <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> Yöntem aşırı yüklemesi herhangi bir nesneyi kabul ettiğinden, temsilcinin kullanılması, verileri geçirmek için tür açısından güvenli bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="20396-120">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="20396-121">Diğer bir seçenek de iş parçacığı yordamını ve verileri bir yardımcı sınıfında kapsüllemek ve <xref:System.Threading.ThreadStart> iş parçacığı yordamını yürütmek için temsilciyi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="20396-121">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="20396-122">Aşağıdaki örnek bu tekniği göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="20396-122">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="20396-123">Ne <xref:System.Threading.ThreadStart> ya da <xref:System.Threading.ParameterizedThreadStart> temsilcinin dönüş değeri yoktur, çünkü verileri zaman uyumsuz bir çağrıdan döndürmek için bir yer yoktur.</span><span class="sxs-lookup"><span data-stu-id="20396-123">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="20396-124">Bir iş parçacığı yönteminin sonuçlarını almak için, sonraki bölümde gösterildiği gibi bir geri çağırma yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20396-124">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="20396-125">Geri çağırma yöntemleriyle iş parçacıklarından veri alma</span><span class="sxs-lookup"><span data-stu-id="20396-125">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="20396-126">Aşağıdaki örnek, bir iş parçacığından veri alan bir geri çağırma yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="20396-126">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="20396-127">Veri ve iş parçacığı yöntemi içeren sınıf için Oluşturucu, geri çağırma yöntemini temsil eden bir temsilciyi de kabul eder; iş parçacığı yöntemi bitmeden önce geri çağırma temsilcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="20396-127">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="20396-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20396-128">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="20396-129">İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="20396-129">Threading</span></span>](index.md)
- [<span data-ttu-id="20396-130">Iş parçacıkları ve Iş parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="20396-130">Using Threads and Threading</span></span>](using-threads-and-threading.md)
