---
title: İş parçacığı oluşturma ve başlatma zamanında veri geçirme
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 028f8b978a7809fa9ae4710ab85d7dc84e7b04fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201887"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="74744-102">İş parçacığı oluşturma ve başlatma zamanında veri geçirme</span><span class="sxs-lookup"><span data-stu-id="74744-102">Creating threads and passing data at start time</span></span>

<span data-ttu-id="74744-103">İşletim sistemi, bir işletim sistemi işlem oluşturulduğunda, özgün tüm uygulama etki alanı da dahil olmak üzere bu işlemde kod yürütmek için bir iş parçacığı ekler.</span><span class="sxs-lookup"><span data-stu-id="74744-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="74744-104">Bu noktadan itibaren uygulama etki alanları oluşturulabilir ve mutlaka yok veya oluşturulan tüm işletim sistemleri iş parçacıkları yok.</span><span class="sxs-lookup"><span data-stu-id="74744-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="74744-105">Yürütülen kod yönetilen kod, bir <xref:System.Threading.Thread> parçacığının geçerli uygulama etki alanında statik alarak elde edilebilir nesnesi <xref:System.Threading.Thread.CurrentThread%2A> türünün özelliği <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="74744-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="74744-106">Bu konu, iş parçacığı oluşturma açıklar ve iş parçacığı yordamı için verileri geçirmek için seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="74744-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="74744-107">Bir iş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="74744-107">Creating a thread</span></span>

 <span data-ttu-id="74744-108">Yeni bir oluşturma <xref:System.Threading.Thread> yeni bir yönetilen iş parçacığı nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74744-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="74744-109"><xref:System.Threading.Thread> Sınıfında alan oluşturucular bir <xref:System.Threading.ThreadStart> temsilci veya <xref:System.Threading.ParameterizedThreadStart> temsilci; çağırdığınızda, yeni iş parçacığı tarafından çağrılan yöntem temsilciye sarmalar <xref:System.Threading.Thread.Start%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="74744-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="74744-110">Çağırma <xref:System.Threading.Thread.Start%2A> birden çok kez neden olan bir <xref:System.Threading.ThreadStateException> oluşturulması için.</span><span class="sxs-lookup"><span data-stu-id="74744-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="74744-111"><xref:System.Threading.Thread.Start%2A> Yöntemi, hemen, genellikle yeni iş parçacığı gerçekten başlatılmadan önce döndürür.</span><span class="sxs-lookup"><span data-stu-id="74744-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="74744-112">Kullanabileceğiniz <xref:System.Threading.Thread.ThreadState%2A> ve <xref:System.Threading.Thread.IsAlive%2A> herhangi bir anda iş parçacığı durumunu belirlemek için özellikleri, ancak bu özellikler hiçbir zaman iş parçacıklarının etkinlikleri eşitlemek için kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="74744-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74744-113">Bir iş parçacığı başlatıldıktan sonra bir başvuru korumak gerekli değildir <xref:System.Threading.Thread> nesne.</span><span class="sxs-lookup"><span data-stu-id="74744-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="74744-114">İş parçacığının iş parçacığı yordamı sonlandırılana kadar yürütmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="74744-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="74744-115">Aşağıdaki kod örneği, örnek ve statik yöntemler, başka bir nesne üzerinde çağırmak için iki yeni iş parçacığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="74744-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="74744-116">İş parçacıklarına veri geçirme</span><span class="sxs-lookup"><span data-stu-id="74744-116">Passing data to threads</span></span>

 <span data-ttu-id="74744-117">.NET Framework sürüm 2.0 <xref:System.Threading.ParameterizedThreadStart> temsilci çağırdığınızda, bir iş parçacığına veri içeren bir nesne geçirmek için kolay bir yol sağlar <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesi.</span><span class="sxs-lookup"><span data-stu-id="74744-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="74744-118">Bkz: <xref:System.Threading.ParameterizedThreadStart> kod örneği için.</span><span class="sxs-lookup"><span data-stu-id="74744-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="74744-119">Kullanarak <xref:System.Threading.ParameterizedThreadStart> temsilci değil veri iletmek için tür açısından güvenli bir şekilde çünkü <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini kabul eden herhangi bir nesne.</span><span class="sxs-lookup"><span data-stu-id="74744-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="74744-120">İş parçacığı yordamı ve yardımcı bir sınıf içindeki verileri kapsüllemek ve kullanmak için bir alternatifidir <xref:System.Threading.ThreadStart> iş parçacığı yordamı yürütmek için temsilci.</span><span class="sxs-lookup"><span data-stu-id="74744-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="74744-121">Aşağıdaki örnek, bu tekniği gösterir:</span><span class="sxs-lookup"><span data-stu-id="74744-121">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="74744-122">Ne <xref:System.Threading.ThreadStart> ya da <xref:System.Threading.ParameterizedThreadStart> temsilcinin dönüş değeri, zaman uyumsuz bir çağrıdan dönüş verileri bir yer olduğundan.</span><span class="sxs-lookup"><span data-stu-id="74744-122">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="74744-123">Bir iş parçacığı yöntem sonuçlarını almak için sonraki bölümde gösterildiği gibi bir geri çağırma yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74744-123">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="74744-124">Geri çağırma yöntemleri ile parçacıklarından veri alma</span><span class="sxs-lookup"><span data-stu-id="74744-124">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="74744-125">Aşağıdaki örnek, bir iş parçacığından verileri alan bir geri arama yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="74744-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="74744-126">Verileri ve iş parçacığı yöntemi içeren sınıf için oluşturucu, aynı zamanda geri çağırma yöntemi temsil eden bir temsilci kabul eder; iş parçacığı yöntemi sona ermeden önce geri çağırma temsilcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="74744-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="74744-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74744-127">See also</span></span>

- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadStart>  
- <xref:System.Threading.ParameterizedThreadStart>  
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="74744-128">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="74744-128">Threading</span></span>](index.md)  
- [<span data-ttu-id="74744-129">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="74744-129">Using Threads and Threading</span></span>](using-threads-and-threading.md)
