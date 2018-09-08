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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddf311ad2b79e615f5c3097686035e7bbfbc49c9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185145"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="824b2-102">Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="824b2-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="824b2-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> aşırı oluşturulabilecek özel durumları işlemek için özel bir mekanizma yoktur.</span><span class="sxs-lookup"><span data-stu-id="824b2-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="824b2-104">Bu bakımdan, bunlar normal benzer `for` ve `foreach` döngüler (`For` ve `For Each` Visual Basic'te); işlenmeyen bir özel durum hemen sonlandırmak döngüye neden oluyor.</span><span class="sxs-lookup"><span data-stu-id="824b2-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="824b2-105">Paralel döngüler, hangi benzer özel durumları birden çok iş parçacığında aynı anda atılabilir harf ve bir iş parçacığı üzerinde oluşturulan bir özel durum başka bir özel durum neden olan durumu işlemek için kendi özel durum işleme mantığı eklerken iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="824b2-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="824b2-106">Tüm özel durumları döngüden sarmalama tarafından her iki durumda işleyebilen bir <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="824b2-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="824b2-107">Aşağıdaki örnekte, olası bir yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="824b2-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="824b2-108">"Yalnızca kendi kodum" etkin olduğunda, bazı durumlarda Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler</span><span class="sxs-lookup"><span data-stu-id="824b2-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="824b2-109">Bu hata zararsızdır.</span><span class="sxs-lookup"><span data-stu-id="824b2-109">This error is benign.</span></span> <span data-ttu-id="824b2-110">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örnekte gösterilen özel durum işleme davranışını bakın.</span><span class="sxs-lookup"><span data-stu-id="824b2-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="824b2-111">Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="824b2-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="824b2-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="824b2-112">Example</span></span>  
 <span data-ttu-id="824b2-113">Bu örnekte, tüm özel durum yakalandı ve ardından içinde sarmalanmış bir <xref:System.AggregateException?displayProperty=nameWithType> hangi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="824b2-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="824b2-114">Çağıran, hangi özel durumları işlemek için karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="824b2-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="824b2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="824b2-115">See also</span></span>

- [<span data-ttu-id="824b2-116">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="824b2-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
- [<span data-ttu-id="824b2-117">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="824b2-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
