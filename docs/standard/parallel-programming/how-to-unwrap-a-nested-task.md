---
title: 'Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: c72654a2bc21035fe706d76018bb163d8ba01ee8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106901"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="221b3-102">Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="221b3-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="221b3-103">Bir görevi bir yöntemden döndürebilir ve aşağıdaki örnekte gösterildiği gibi bu görevi bekleyebilir veya bu görevden devam edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="221b3-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="221b3-104">Önceki örnekte, <xref:System.Threading.Tasks.Task%601.Result%2A> özellik tür `string` (Visual`String` Basic' de).</span><span class="sxs-lookup"><span data-stu-id="221b3-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="221b3-105">Ancak, bazı senaryolarda, başka bir görev içinde bir görev oluşturmak ve sonra iç içe görev dönmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="221b3-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="221b3-106">Bu durumda, `TResult` çevreleyen görevin kendisi bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="221b3-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="221b3-107">Aşağıdaki örnekte, Sonuç özelliği `Task<Task<string>>` C#'da `Task(Of Task(Of String))` veya Visual Basic'te dir.</span><span class="sxs-lookup"><span data-stu-id="221b3-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="221b3-108">Dış görevin paketlerini açmak ve özgün görevi ve özelliğini <xref:System.Threading.Tasks.Task%601.Result%2A> almak için kod yazmak mümkün olsa da, özel durumları ve ayrıca iptal isteklerini işlemeniz gerektiğinden bu kodu yazmak kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="221b3-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="221b3-109">Bu durumda, aşağıdaki örnekte gösterildiği <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> gibi uzantı yöntemlerinden birini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="221b3-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="221b3-110">Bu <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> yöntemler, herhangi bir `Task<Task>` `Task<Task<TResult>>` veya`Task(Of Task)` `Task(Of Task(Of TResult))` (veya Visual Basic'te) bir `Task` veya `Task<TResult>` (Visual`Task(Of TResult)` Basic) dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="221b3-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="221b3-111">Yeni görev iç içe geçme görevini tam olarak temsil eder ve iptal durumunu ve tüm özel durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="221b3-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="221b3-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="221b3-112">Example</span></span>  
 <span data-ttu-id="221b3-113">Aşağıdaki örnek, uzantı yöntemlerinin nasıl kullanılacağını <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="221b3-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="221b3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="221b3-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="221b3-115">Görev Tabanlı Zaman Uyumsuz Desen</span><span class="sxs-lookup"><span data-stu-id="221b3-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
