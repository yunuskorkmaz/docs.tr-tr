---
title: 'Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
ms.openlocfilehash: 5ccddfb01d6b173900dfffc465292c7812626ddc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587981"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a><span data-ttu-id="5731a-102">Nasıl yapılır: PLINQ Sorgusunda Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="5731a-102">How to: Handle Exceptions in a PLINQ Query</span></span>

<span data-ttu-id="5731a-103">Bu konudaki ilk örnek, bir <xref:System.AggregateException?displayProperty=nameWithType> PLINQ sorgusundan yürütüldüğünde atılabilir nasıl işleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5731a-103">The first example in this topic shows how to handle the <xref:System.AggregateException?displayProperty=nameWithType> that can be thrown from a PLINQ query when it executes.</span></span> <span data-ttu-id="5731a-104">İkinci örnek, özel durum atılacağına mümkün olduğunca yakın, temsilciler içinde try-catch blokları koymak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="5731a-104">The second example shows how to put try-catch blocks within delegates, as close as possible to where the exception will be thrown.</span></span> <span data-ttu-id="5731a-105">Bu şekilde, bunları en kısa sürede onlar meydana gelir gelmez yakalamak ve büyük olasılıkla sorgu yürütme devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5731a-105">In this way, you can catch them as soon as they occur and possibly continue query execution.</span></span> <span data-ttu-id="5731a-106">Özel durumların birleştirme iş parçacığına geri dönmesine izin verildiğinde, özel durum yükseltildikten sonra bir sorgunun bazı öğeleri işlemeye devam etmesi mümkündür.</span><span class="sxs-lookup"><span data-stu-id="5731a-106">When exceptions are allowed to bubble up back to the joining thread, then it is possible that a query may continue to process some items after the exception is raised.</span></span>

<span data-ttu-id="5731a-107">PlinQ'un sıralı yürütmeye geri düştüğü ve bir özel durum oluştuğu bazı durumlarda, özel durum <xref:System.AggregateException>doğrudan yayılabilir ve bir .</span><span class="sxs-lookup"><span data-stu-id="5731a-107">In some cases when PLINQ falls back to sequential execution, and an exception occurs, the exception may be propagated directly, and not wrapped in an <xref:System.AggregateException>.</span></span> <span data-ttu-id="5731a-108">Ayrıca, <xref:System.Threading.ThreadAbortException>s her zaman doğrudan yayılır.</span><span class="sxs-lookup"><span data-stu-id="5731a-108">Also, <xref:System.Threading.ThreadAbortException>s are always propagated directly.</span></span>

> [!NOTE]
> <span data-ttu-id="5731a-109">"Yalnızca Kodum" etkinleştirildiğinde, Visual Studio özel durumu atan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5731a-109">When "Just My Code" is enabled, Visual Studio will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="5731a-110">Bu hata iyi huylu.</span><span class="sxs-lookup"><span data-stu-id="5731a-110">This error is benign.</span></span> <span data-ttu-id="5731a-111">Devam etmek için F5 tuşuna basabilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5731a-111">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="5731a-112">Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5731a-112">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>
>
> <span data-ttu-id="5731a-113">Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="5731a-113">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="5731a-114">Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5731a-114">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>

## <a name="example"></a><span data-ttu-id="5731a-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="5731a-115">Example</span></span>

<span data-ttu-id="5731a-116">Bu örnek, atılan <xref:System.AggregateException?displayProperty=nameWithType>s'leri yakalamak için sorguyu yürüten kodun etrafına try-catch bloklarının nasıl yerleştirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5731a-116">This example shows how to put the try-catch blocks around the code that executes the query to catch any <xref:System.AggregateException?displayProperty=nameWithType>s that are thrown.</span></span>

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

<span data-ttu-id="5731a-117">Bu örnekte, özel durum atıldıktan sonra sorgu devam edemez.</span><span class="sxs-lookup"><span data-stu-id="5731a-117">In this example, the query cannot continue after the exception is thrown.</span></span> <span data-ttu-id="5731a-118">Uygulama kodunuz özel durumu yakaladığında, PLINQ tüm iş parçacıklarındaki sorguyu zaten durdurmuştur.</span><span class="sxs-lookup"><span data-stu-id="5731a-118">By the time your application code catches the exception, PLINQ has already stopped the query on all threads.</span></span>

## <a name="example"></a><span data-ttu-id="5731a-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="5731a-119">Example</span></span>

<span data-ttu-id="5731a-120">Aşağıdaki örnek, bir özel durum yakalamak ve sorgu yürütme ile devam etmek mümkün kılmak için bir temsilci bir try-catch blok koymak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="5731a-120">The following example shows how to put a try-catch block in a delegate to make it possible to catch an exception and continue with the query execution.</span></span>

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a><span data-ttu-id="5731a-121">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5731a-121">Compiling the Code</span></span>

- <span data-ttu-id="5731a-122">Bu örnekleri derlemek ve çalıştırmak için bunları PLINQ Veri Örneği örneğine kopyalayın ve yöntemi Main'den arayın.</span><span class="sxs-lookup"><span data-stu-id="5731a-122">To compile and run these examples, copy them into the PLINQ Data Sample example and call the method from Main.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="5731a-123">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="5731a-123">Robust Programming</span></span>

<span data-ttu-id="5731a-124">Programınızın durumunu bozmamak için nasıl işleyeceğinizkonusunda bir özel durum yakalamayın.</span><span class="sxs-lookup"><span data-stu-id="5731a-124">Do not catch an exception unless you know how to handle it so that you do not corrupt the state of your program.</span></span>

## <a name="see-also"></a><span data-ttu-id="5731a-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5731a-125">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="5731a-126">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="5731a-126">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
