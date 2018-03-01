---
title: "Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme"
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
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f6df28a019c2a21cc6ef94367553e0e5eaa1ad30
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="618de-102">Nasıl yapılır: Paralel Döngülerde Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="618de-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="618de-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> aşırı durum özel durumları işlemek için herhangi bir özel mekanizma sahip değil.</span><span class="sxs-lookup"><span data-stu-id="618de-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="618de-104">Bu bakımdan, bunlar normal benzer `for` ve `foreach` döngüleri (`For` ve `For Each` Visual Basic'te); işlenmeyen bir özel durum hemen sonlandırmak döngü neden olur.</span><span class="sxs-lookup"><span data-stu-id="618de-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="618de-105">Paralel döngüler, hangi benzer birden çok iş parçacığı üzerinde eşzamanlı olarak özel durumlar çalışması ve bir iş parçacığı üzerinde oluşturulan bir özel başka bir durum başka bir özel duruma neden olan durumu işlemek için kendi özel durum işleme mantığı eklediğinizde iş parçacığı.</span><span class="sxs-lookup"><span data-stu-id="618de-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="618de-106">Döngüde tüm özel durumlar kaydırma tarafından her iki durumda işleyebilecek bir <xref:System.AggregateException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="618de-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="618de-107">Aşağıdaki örnek, bir olası yaklaşım gösterir.</span><span class="sxs-lookup"><span data-stu-id="618de-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="618de-108">"Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio bazı durumlarda, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir</span><span class="sxs-lookup"><span data-stu-id="618de-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="618de-109">Bu hata zararsız kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="618de-109">This error is benign.</span></span> <span data-ttu-id="618de-110">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örnekte gösterilen özel durum işleme davranışı bakın.</span><span class="sxs-lookup"><span data-stu-id="618de-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="618de-111">Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="618de-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="618de-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="618de-112">Example</span></span>  
 <span data-ttu-id="618de-113">Bu örnekte, tüm özel durum yakalandı ve ardından sarmalanmış bir <xref:System.AggregateException?displayProperty=nameWithType> hangi oluşur.</span><span class="sxs-lookup"><span data-stu-id="618de-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="618de-114">Arayan hangi özel durumları işlemek için karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="618de-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="618de-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="618de-115">See Also</span></span>  
 [<span data-ttu-id="618de-116">Veri Paralelliği</span><span class="sxs-lookup"><span data-stu-id="618de-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [<span data-ttu-id="618de-117">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="618de-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
