---
title: 'Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme'
description: .NET 'teki paralel Döngülerde özel durumları nasıl işleyeceğinizi öğrenin. Bir System. AggregateException içindeki döngüden tüm özel durumların nasıl sarılacağını gösteren bir örnek görürsünüz.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: 61c22d6e82282f8aeb54818c813d4489e3bc9641
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768982"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="39a50-104">Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="39a50-104">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="39a50-105"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> aşırı yüklemelerin, oluşturulan özel durumları işlemek için özel bir mekanizması yoktur.</span><span class="sxs-lookup"><span data-stu-id="39a50-105">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="39a50-106">Bu şekilde, düzenli `for` ve `foreach` döngülere ( `For` ve `For Each` Visual Basic) benzeirler; işlenmeyen bir özel durum, çalışmakta olan tüm yinelemeler sona erdiğinde döngünün sonlandırılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="39a50-106">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="39a50-107">Paralel döngülere kendi özel durum işleme mantığınızı eklediğinizde, benzer özel durumların aynı anda birden çok iş parçacığında oluşturulması ve bir iş parçacığında oluşan bir özel durumun başka bir iş parçacığında başka bir özel durumun oluşturulmasına neden olduğu büyük/küçük harf işleme.</span><span class="sxs-lookup"><span data-stu-id="39a50-107">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="39a50-108">İçindeki döngüden tüm özel durumları sarmalayarak her iki durumu da işleyebilirsiniz <xref:System.AggregateException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="39a50-108">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="39a50-109">Aşağıdaki örnekte olası bir yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="39a50-109">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39a50-110">"Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="39a50-110">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="39a50-111">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="39a50-111">This error is benign.</span></span> <span data-ttu-id="39a50-112">F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örnekte gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="39a50-112">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="39a50-113">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="39a50-113">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39a50-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="39a50-114">Example</span></span>  
 <span data-ttu-id="39a50-115">Bu örnekte, tüm özel durumlar yakalandıktan sonra bir <xref:System.AggregateException?displayProperty=nameWithType> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="39a50-115">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="39a50-116">Çağıran, hangi özel durumların işleneceğini karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="39a50-116">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="39a50-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39a50-117">See also</span></span>

- [<span data-ttu-id="39a50-118">Veri paralelliği</span><span class="sxs-lookup"><span data-stu-id="39a50-118">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="39a50-119">PLıNQ ve TPL 'deki lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="39a50-119">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
