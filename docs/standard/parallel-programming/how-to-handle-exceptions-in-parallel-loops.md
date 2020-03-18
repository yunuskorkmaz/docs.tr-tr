---
title: 'Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 5d108937e6ab2483cd1633d4b398c1e250f5c098
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77453019"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="6a413-102">Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="6a413-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="6a413-103">Ve <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> aşırı yüklemeler, atılabilecek özel durumları işlemek için özel bir mekanizmaya sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="6a413-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="6a413-104">Bu bakımdan, normal `for` `foreach` ve döngülere benzerler (`For` ve `For Each` Visual Basic'te); işlenmemiş bir özel durum, şu anda çalışan tüm yinelemeler biter bitmez döngünün sonlandırılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6a413-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="6a413-105">Paralel döngülere kendi özel durum işleme mantığınızı eklediğinizde, aynı anda birden çok iş parçacığına benzer özel durumların atılabileceği ve bir iş parçacığına atılan özel durumun başka bir özel durum diğerine atılmasına neden olduğu durumu işleme Iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="6a413-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="6a413-106">Döngüdeki tüm özel durumları bir <xref:System.AggregateException?displayProperty=nameWithType>'de saran her iki servis vakasını da işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a413-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6a413-107">Aşağıdaki örnek, olası bir yaklaşımı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6a413-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a413-108">"Yalnızca Kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6a413-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="6a413-109">Bu hata iyi huylu.</span><span class="sxs-lookup"><span data-stu-id="6a413-109">This error is benign.</span></span> <span data-ttu-id="6a413-110">Devam etmek için F5 tuşuna basabilir ve aşağıdaki örnekte gösterilen özel durum işleme davranışını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6a413-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="6a413-111">Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="6a413-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a413-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="6a413-112">Example</span></span>  
 <span data-ttu-id="6a413-113">Bu örnekte, tüm özel durumlar yakalanır ve <xref:System.AggregateException?displayProperty=nameWithType> sonra atılan bir sarılır.</span><span class="sxs-lookup"><span data-stu-id="6a413-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="6a413-114">Arayan, hangi özel durumların işleyeceğini belirleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6a413-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="6a413-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a413-115">See also</span></span>

- [<span data-ttu-id="6a413-116">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="6a413-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="6a413-117">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="6a413-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
