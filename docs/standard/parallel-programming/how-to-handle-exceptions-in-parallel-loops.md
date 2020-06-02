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
ms.openlocfilehash: 87405425e85ed16d10b3e8b382c6e414fff10ddf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278538"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="19548-102">Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="19548-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="19548-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> aşırı yüklemelerin, oluşturulan özel durumları işlemek için özel bir mekanizması yoktur.</span><span class="sxs-lookup"><span data-stu-id="19548-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="19548-104">Bu şekilde, düzenli `for` ve `foreach` döngülere ( `For` ve `For Each` Visual Basic) benzeirler; işlenmeyen bir özel durum, çalışmakta olan tüm yinelemeler sona erdiğinde döngünün sonlandırılmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="19548-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate as soon as all currently running iterations finish.</span></span>
  
 <span data-ttu-id="19548-105">Paralel döngülere kendi özel durum işleme mantığınızı eklediğinizde, benzer özel durumların aynı anda birden çok iş parçacığında oluşturulması ve bir iş parçacığında oluşan bir özel durumun başka bir iş parçacığında başka bir özel durumun oluşturulmasına neden olduğu büyük/küçük harf işleme.</span><span class="sxs-lookup"><span data-stu-id="19548-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="19548-106">İçindeki döngüden tüm özel durumları sarmalayarak her iki durumu da işleyebilirsiniz <xref:System.AggregateException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="19548-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="19548-107">Aşağıdaki örnekte olası bir yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="19548-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19548-108">"Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="19548-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="19548-109">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="19548-109">This error is benign.</span></span> <span data-ttu-id="19548-110">F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örnekte gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19548-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="19548-111">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="19548-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19548-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="19548-112">Example</span></span>  
 <span data-ttu-id="19548-113">Bu örnekte, tüm özel durumlar yakalandıktan sonra bir <xref:System.AggregateException?displayProperty=nameWithType> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="19548-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="19548-114">Çağıran, hangi özel durumların işleneceğini karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="19548-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="19548-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19548-115">See also</span></span>

- [<span data-ttu-id="19548-116">Veri paralelliği</span><span class="sxs-lookup"><span data-stu-id="19548-116">Data Parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="19548-117">PLıNQ ve TPL 'deki lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="19548-117">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
