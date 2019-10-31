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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106901"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="557db-102">Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="557db-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="557db-103">Aşağıdaki örnekte gösterildiği gibi, bir yöntemden bir görev döndürebilir ve sonra bu görevden bekleyebilir veya devam edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="557db-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="557db-104">Önceki örnekte <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği `string` türündedir (`String` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="557db-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="557db-105">Ancak, bazı senaryolarda başka bir görevde bir görev oluşturmak ve ardından iç içe görevi döndürmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="557db-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="557db-106">Bu durumda, kapsayan görevin `TResult` kendisi bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="557db-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="557db-107">Aşağıdaki örnekte Result özelliği Visual Basic içinde C# veya `Task(Of Task(Of String))` `Task<Task<string>>`.</span><span class="sxs-lookup"><span data-stu-id="557db-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="557db-108">Dış görevin sarmalarını kaldırmak ve özgün görevi ve <xref:System.Threading.Tasks.Task%601.Result%2A> özelliğini almak için kod yazmak mümkün olsa da, özel durumları ve ayrıca iptal isteklerini işleyebilmeniz gerektiğinden, bu tür kodun yazılması kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="557db-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="557db-109">Bu durumda, aşağıdaki örnekte gösterildiği gibi <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> uzantısı yöntemlerinden birini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="557db-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="557db-110"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Yöntemler `Task<Task>` veya `Task<Task<TResult>>``Task(Of Task)` (`Task(Of Task(Of TResult))`) Visual Basic veya `Task` (`Task<TResult>``Task(Of TResult)`) arasında dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="557db-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="557db-111">Yeni görev iç iç içe görevi tamamen temsil eder ve iptal durumu ve tüm özel durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="557db-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="557db-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="557db-112">Example</span></span>  
 <span data-ttu-id="557db-113">Aşağıdaki örnek, <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> uzantısı yöntemlerinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="557db-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="557db-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="557db-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="557db-115">Görev Tabanlı Zaman Uyumsuz Desen</span><span class="sxs-lookup"><span data-stu-id="557db-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
