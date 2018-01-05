---
title: "Başlatma Zamanında İş Parçacığı Oluşturma ve Veri Geçirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d17ef8a199061f56f00e39fa887e2e64f64427ec
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="cf429-102">Başlatma Zamanında İş Parçacığı Oluşturma ve Veri Geçirme</span><span class="sxs-lookup"><span data-stu-id="cf429-102">Creating Threads and Passing Data at Start Time</span></span>
<span data-ttu-id="cf429-103">Bir işletim sistemi işlem oluşturulduğunda, işletim sistemi herhangi bir özgün uygulama etki alanı dahil olmak üzere bu işlemde kod yürütmek için bir iş parçacığı yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="cf429-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="cf429-104">Bu noktadan itibaren uygulama etki alanları oluşturulur ve mutlaka oluşturulma veya yok tüm işletim sistemi iş parçacıkları yok.</span><span class="sxs-lookup"><span data-stu-id="cf429-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="cf429-105">Yürütülen kod yönetiliyorsa kod, sonra bir <xref:System.Threading.Thread> geçerli uygulama etki alanında iş parçacığının statik alarak elde edilebilir için nesne <xref:System.Threading.Thread.CurrentThread%2A> türündeki özelliği <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="cf429-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="cf429-106">Bu konu, iş parçacığı oluşturma açıklar ve iş parçacığı yordamı veri geçirme için seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf429-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="cf429-107">Bir iş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf429-107">Creating a Thread</span></span>  
 <span data-ttu-id="cf429-108">Yeni bir oluşturma <xref:System.Threading.Thread> yeni bir yönetilen iş parçacığı nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf429-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="cf429-109"><xref:System.Threading.Thread> Sınıfına sahip olması oluşturucular bir <xref:System.Threading.ThreadStart> temsilci veya <xref:System.Threading.ParameterizedThreadStart> temsilci; çağırdığınızda yeni iş parçacığı tarafından çağrılan yöntemin temsilci sarmalar <xref:System.Threading.Thread.Start%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf429-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="cf429-110">Çağırma <xref:System.Threading.Thread.Start%2A> birden çok kez neden olan bir <xref:System.Threading.ThreadStateException> oluşturulmasına.</span><span class="sxs-lookup"><span data-stu-id="cf429-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="cf429-111"><xref:System.Threading.Thread.Start%2A> Yöntemi, hemen, genellikle yeni bir iş parçacığı gerçekten başlatılmadan önce döndürür.</span><span class="sxs-lookup"><span data-stu-id="cf429-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="cf429-112">Kullanabileceğiniz <xref:System.Threading.Thread.ThreadState%2A> ve <xref:System.Threading.Thread.IsAlive%2A> iş parçacığı herhangi bir anda durumunu belirlemek için özellikler, ancak bu özellikler hiçbir iş parçacığı etkinliklerini eşitlemek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cf429-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf429-113">Bir iş parçacığı başladıktan sonra bir başvuru korumak gerekli değildir <xref:System.Threading.Thread> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="cf429-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="cf429-114">İş parçacığı için iş parçacığı yordamı sonlanana kadar yürütmeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="cf429-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="cf429-115">Aşağıdaki kod örneği başka bir nesne üzerinde örnek ve statik yöntemleri çağırmak için iki yeni iş parçacığı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cf429-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a><span data-ttu-id="cf429-116">İş parçacıklarına veri geçirme ve parçacıklarından veri alma</span><span class="sxs-lookup"><span data-stu-id="cf429-116">Passing Data to Threads and Retrieving Data from Threads</span></span>  
 <span data-ttu-id="cf429-117">.NET Framework sürüm 2.0, <xref:System.Threading.ParameterizedThreadStart> temsilci çağırdığınızda bir iş parçacığı verileri içeren bir nesne geçirmek için kolay bir yol sağlar <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini.</span><span class="sxs-lookup"><span data-stu-id="cf429-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="cf429-118">Bkz: <xref:System.Threading.ParameterizedThreadStart> için bir kod örneğidir.</span><span class="sxs-lookup"><span data-stu-id="cf429-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="cf429-119">Kullanarak <xref:System.Threading.ParameterizedThreadStart> temsilci değil veri iletmek için bir tür kullanımı uyumlu şekilde çünkü <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> yöntemi aşırı yüklemesini kabul eden herhangi bir nesne.</span><span class="sxs-lookup"><span data-stu-id="cf429-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="cf429-120">İş parçacığı yordamı ve bir yardımcı sınıfı verileri şifreleyebilir ve kullanmak için bir alternatif olan <xref:System.Threading.ThreadStart> iş parçacığı yordamı yürütmek için temsilci.</span><span class="sxs-lookup"><span data-stu-id="cf429-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="cf429-121">Bu teknik izleyen iki kod örnekleri gösterilir.</span><span class="sxs-lookup"><span data-stu-id="cf429-121">This technique is shown in the two code examples that follow.</span></span>  
  
 <span data-ttu-id="cf429-122">Hiçbirini temsilcileri olan dönüş değeri, zaman uyumsuz çağrısından verileri döndürmek için hiçbir yerde olduğundan.</span><span class="sxs-lookup"><span data-stu-id="cf429-122">Neither of these delegates has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="cf429-123">Bir iş parçacığı yöntem sonuçlarını almak için ikinci kod örneğinde gösterildiği gibi bir geri çağırma yöntemi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf429-123">To retrieve the results of a thread method, you can use a callback method, as demonstrated in the second code example.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a><span data-ttu-id="cf429-124">Geri arama yöntemleri ile veri alma</span><span class="sxs-lookup"><span data-stu-id="cf429-124">Retrieving Data with Callback Methods</span></span>  
 <span data-ttu-id="cf429-125">Aşağıdaki örnek, bir iş parçacığından veri alan geri arama yöntemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="cf429-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="cf429-126">Verileri ve iş parçacığı yöntemi içeren sınıf oluşturucusu geri çağırma yöntemi temsil eden bir temsilci de kabul eder; iş parçacığı yöntemi sona ermeden önce geri çağırma temsilcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="cf429-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="cf429-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf429-127">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="cf429-128">İş parçacığı oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf429-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="cf429-129">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="cf429-129">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
