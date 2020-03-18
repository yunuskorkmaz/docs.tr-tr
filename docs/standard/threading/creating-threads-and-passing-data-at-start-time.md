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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138097"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="2faa3-102">Başlatma zamanında iş parçacığı oluşturma ve veri geçirme</span><span class="sxs-lookup"><span data-stu-id="2faa3-102">Creating threads and passing data at start time</span></span>

<span data-ttu-id="2faa3-103">Bir işletim sistemi işlemi oluşturulduğunda, işletim sistemi herhangi bir özgün uygulama etki alanı da dahil olmak üzere, bu işlemde kodu yürütmek için bir iş parçacığı enjekte eder.</span><span class="sxs-lookup"><span data-stu-id="2faa3-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="2faa3-104">Bu noktadan itibaren, uygulama etki alanları oluşturulabilir ve herhangi bir işletim sistemi iş parçacığı mutlaka oluşturulma veya yok olmadan yok.</span><span class="sxs-lookup"><span data-stu-id="2faa3-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="2faa3-105">Yürütülen kod yönetilirse, <xref:System.Threading.Thread> geçerli uygulama etki alanında çalıştırılan iş parçacığı için bir <xref:System.Threading.Thread.CurrentThread%2A> nesne türü <xref:System.Threading.Thread>statik özelliği alınarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="2faa3-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="2faa3-106">Bu konu iş parçacığı oluşturma açıklar ve iş parçacığı yordamına veri aktarmak için alternatifleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="2faa3-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="2faa3-107">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="2faa3-107">Creating a thread</span></span>

 <span data-ttu-id="2faa3-108">Yeni <xref:System.Threading.Thread> bir nesne oluşturmak yeni yönetilen iş parçacığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2faa3-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="2faa3-109">Sınıfın <xref:System.Threading.Thread> bir <xref:System.Threading.ThreadStart> temsilci veya <xref:System.Threading.ParameterizedThreadStart> temsilci alan oluşturucuları vardır; temsilci, <xref:System.Threading.Thread.Start%2A> yöntemi çağırdığınızda yeni iş parçacığı tarafından çağrılan yöntemi sarar.</span><span class="sxs-lookup"><span data-stu-id="2faa3-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="2faa3-110">Birden <xref:System.Threading.Thread.Start%2A> fazla kez <xref:System.Threading.ThreadStateException> aramak bir atılmasını neden olur.</span><span class="sxs-lookup"><span data-stu-id="2faa3-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="2faa3-111">Yöntem, <xref:System.Threading.Thread.Start%2A> genellikle yeni iş parçacığı gerçekten başlamadan önce hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="2faa3-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="2faa3-112">İş parçacığının <xref:System.Threading.Thread.ThreadState%2A> <xref:System.Threading.Thread.IsAlive%2A> durumunu herhangi bir anda belirlemek için ve özellikleri kullanabilirsiniz, ancak bu özellikler iş parçacıklarının etkinliklerini eşitlemek için asla kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2faa3-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2faa3-113">Bir iş parçacığı başlatıldıktan sonra, <xref:System.Threading.Thread> nesneye bir başvuru tutmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2faa3-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="2faa3-114">İş parçacığı yordamı sona erene kadar iş parçacığı yürütmeye devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="2faa3-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="2faa3-115">Aşağıdaki kod örneği, başka bir nesne üzerinde örnek ve statik yöntemleri çağırmak için iki yeni iş parçacığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2faa3-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="2faa3-116">İş parçacıklarına veri aktarma</span><span class="sxs-lookup"><span data-stu-id="2faa3-116">Passing data to threads</span></span>

 <span data-ttu-id="2faa3-117">.NET Framework sürüm <xref:System.Threading.ParameterizedThreadStart> 2.0'da, damad, <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemaşırı yüklemeyi çağırdığınızda veri içeren bir nesneyi iş parçacığına geçirmek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2faa3-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="2faa3-118">Kod <xref:System.Threading.ParameterizedThreadStart> örneği için bkz.</span><span class="sxs-lookup"><span data-stu-id="2faa3-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="2faa3-119">Delektin <xref:System.Threading.ParameterizedThreadStart> kullanılması veri aktarmak için tür <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> güvenli bir yol değildir, çünkü yöntem aşırı yük herhangi bir nesneyi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="2faa3-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="2faa3-120">Bir alternatif iş parçacığı yordamı ve verileri bir yardımcı sınıfta kapsüllemek ve iş parçacığı yordamını yürütmek için <xref:System.Threading.ThreadStart> temsilci kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="2faa3-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="2faa3-121">Aşağıdaki örnekte bu tekniği gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="2faa3-121">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="2faa3-122">Ne <xref:System.Threading.ThreadStart> <xref:System.Threading.ParameterizedThreadStart> de temsilcinin bir geri dönüş değeri vardır, çünkü eşzamanlı bir çağrıdan verileri döndürecek bir yer yoktur.</span><span class="sxs-lookup"><span data-stu-id="2faa3-122">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="2faa3-123">İş parçacığı yönteminin sonuçlarını almak için, bir sonraki bölümde gösterildiği gibi bir geri arama yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2faa3-123">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="2faa3-124">Geri arama yöntemleriyle iş parçacığından veri alma</span><span class="sxs-lookup"><span data-stu-id="2faa3-124">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="2faa3-125">Aşağıdaki örnek, iş parçacığından veri alan bir geri arama yöntemini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2faa3-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="2faa3-126">Verileri ve iş parçacığı yöntemini içeren sınıfın oluşturucusu da geri arama yöntemini temsil eden bir temsilci yi kabul eder; iş parçacığı yöntemi sona ermeden önce, geri arama temsilci çağırır.</span><span class="sxs-lookup"><span data-stu-id="2faa3-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2faa3-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2faa3-127">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2faa3-128">İş Parçacığı Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2faa3-128">Threading</span></span>](index.md)
- [<span data-ttu-id="2faa3-129">İş Parçacığı ve İş Parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="2faa3-129">Using Threads and Threading</span></span>](using-threads-and-threading.md)
