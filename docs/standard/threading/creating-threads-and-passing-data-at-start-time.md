---
title: Başlatma zamanında iş parçacığı oluşturma ve veri geçirme
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
ms.openlocfilehash: a628cbb4c9ec8e1c9ccd9fd73e72a82ecf2b2836
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138097"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="2f6a6-102">Başlatma zamanında iş parçacığı oluşturma ve veri geçirme</span><span class="sxs-lookup"><span data-stu-id="2f6a6-102">Creating threads and passing data at start time</span></span>

<span data-ttu-id="2f6a6-103">Bir işletim sistemi işlemi oluşturulduğunda, işletim sistemi, özgün uygulama etki alanı dahil olmak üzere, bu işlemdeki kodu yürütmek için bir iş parçacığını çıkartır.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="2f6a6-104">Bu noktadan itibaren, uygulama etki alanları, herhangi bir işletim sistemi iş parçacığı oluşturulması veya yok olması gerekmeden oluşturulabilir ve yok edilebilir.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="2f6a6-105">Yürütülen kod yönetilen kod ise, geçerli uygulama etki alanında yürütülen iş parçacığının <xref:System.Threading.Thread> nesnesi, <xref:System.Threading.Thread>türündeki statik <xref:System.Threading.Thread.CurrentThread%2A> özelliği aracılığıyla elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="2f6a6-106">Bu konu, iş parçacığı oluşturma işlemini açıklar ve iş parçacığı yordamına veri geçirme alternatiflerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="2f6a6-107">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f6a6-107">Creating a thread</span></span>

 <span data-ttu-id="2f6a6-108">Yeni bir <xref:System.Threading.Thread> nesnesi oluşturma yeni bir yönetilen iş parçacığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="2f6a6-109"><xref:System.Threading.Thread> sınıfı, bir <xref:System.Threading.ThreadStart> temsilcisi veya <xref:System.Threading.ParameterizedThreadStart> temsilcisi alan oluşturuculara sahiptir; temsilci, <xref:System.Threading.Thread.Start%2A> yöntemini çağırdığınızda yeni iş parçacığı tarafından çağrılan yöntemi sarmalanmış.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="2f6a6-110"><xref:System.Threading.Thread.Start%2A> birden çok kez çağırmak <xref:System.Threading.ThreadStateException> oluşturulmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="2f6a6-111"><xref:System.Threading.Thread.Start%2A> yöntemi hemen, genellikle yeni iş parçacığı başlamadan önce döndürülür.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="2f6a6-112">İş parçacığının durumunu herhangi bir anda anlamak için <xref:System.Threading.Thread.ThreadState%2A> ve <xref:System.Threading.Thread.IsAlive%2A> özelliklerini kullanabilirsiniz, ancak bu özellikler hiçbir zaman iş parçacığı etkinliklerini eşitlemek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f6a6-113">Bir iş parçacığı başlatıldıktan sonra, <xref:System.Threading.Thread> nesnesine bir başvuru tutulması gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="2f6a6-114">İş parçacığı yordamı sona erene kadar iş parçacığı yürütülmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="2f6a6-115">Aşağıdaki kod örneği, başka bir nesne üzerinde örnek ve statik yöntemleri çağırmak için iki yeni iş parçacığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="2f6a6-116">İş parçacıklarına veri geçirme</span><span class="sxs-lookup"><span data-stu-id="2f6a6-116">Passing data to threads</span></span>

 <span data-ttu-id="2f6a6-117">.NET Framework sürüm 2,0 ' de, <xref:System.Threading.ParameterizedThreadStart> temsilci <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntem aşırı yüklemesini çağırdığınızda bir iş parçacığına veri içeren bir nesneyi geçirmek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="2f6a6-118">Kod örneği için <xref:System.Threading.ParameterizedThreadStart> bakın.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="2f6a6-119"><xref:System.Threading.ParameterizedThreadStart> temsilcinin kullanılması, verileri geçirmek için tür açısından güvenli bir yoldur; çünkü <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi herhangi bir nesneyi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="2f6a6-120">Diğer bir seçenek de iş parçacığı yordamını ve verileri bir yardımcı sınıfında kapsüllemek ve iş parçacığı yordamını yürütmek için <xref:System.Threading.ThreadStart> temsilcisini kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="2f6a6-121">Aşağıdaki örnek bu tekniği göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="2f6a6-121">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="2f6a6-122">Bir zaman uyumsuz çağrıdan verileri döndürmek için hiçbir yer olmadığından <xref:System.Threading.ThreadStart> ve <xref:System.Threading.ParameterizedThreadStart> temsilcisinin dönüş değeri yoktur.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-122">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="2f6a6-123">Bir iş parçacığı yönteminin sonuçlarını almak için, sonraki bölümde gösterildiği gibi bir geri çağırma yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-123">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="2f6a6-124">Geri çağırma yöntemleriyle iş parçacıklarından veri alma</span><span class="sxs-lookup"><span data-stu-id="2f6a6-124">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="2f6a6-125">Aşağıdaki örnek, bir iş parçacığından veri alan bir geri çağırma yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="2f6a6-126">Veri ve iş parçacığı yöntemi içeren sınıf için Oluşturucu, geri çağırma yöntemini temsil eden bir temsilciyi de kabul eder; iş parçacığı yöntemi bitmeden önce geri çağırma temsilcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2f6a6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f6a6-127">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2f6a6-128">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2f6a6-128">Threading</span></span>](index.md)
- [<span data-ttu-id="2f6a6-129">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="2f6a6-129">Using Threads and Threading</span></span>](using-threads-and-threading.md)
