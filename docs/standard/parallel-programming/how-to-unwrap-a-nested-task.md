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
ms.openlocfilehash: 9a69fa42da41ee4a071a6571042fd96fb5a009d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288036"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="d61e3-102">Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="d61e3-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="d61e3-103">Aşağıdaki örnekte gösterildiği gibi, bir yöntemden bir görev döndürebilir ve sonra bu görevden bekleyebilir veya devam edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d61e3-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="d61e3-104">Önceki örnekte, <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği türündedir `string` ( `String` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d61e3-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="d61e3-105">Ancak, bazı senaryolarda başka bir görevde bir görev oluşturmak ve ardından iç içe görevi döndürmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d61e3-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="d61e3-106">Bu durumda, `TResult` kapsayan görevin kendisi bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="d61e3-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="d61e3-107">Aşağıdaki örnekte Result özelliği `Task<Task<string>>` C# dilinde veya `Task(Of Task(Of String))` Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d61e3-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="d61e3-108">Dış görevin sarmalaması geri almak ve özgün görevi ve özelliğini almak üzere kod yazmak mümkün olsa da <xref:System.Threading.Tasks.Task%601.Result%2A> , özel durumları ve iptal isteklerini işlemeniz gerektiğinden, bu tür kodun yazılması kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="d61e3-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="d61e3-109">Bu durumda, <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Aşağıdaki örnekte gösterildiği gibi, uzantı yöntemlerinden birini kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="d61e3-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="d61e3-110">Yöntemler, veya <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> `Task<Task>` `Task<Task<TResult>>` ( `Task(Of Task)` `Task(Of Task(Of TResult))` Visual Basic) bir veya ' a ( `Task` `Task<TResult>` `Task(Of TResult)` Visual Basic) dönüştürmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d61e3-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="d61e3-111">Yeni görev iç iç içe görevi tamamen temsil eder ve iptal durumu ve tüm özel durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="d61e3-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d61e3-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d61e3-112">Example</span></span>  
 <span data-ttu-id="d61e3-113">Aşağıdaki örnek, genişletme yöntemlerinin nasıl kullanılacağını göstermektedir <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> .</span><span class="sxs-lookup"><span data-stu-id="d61e3-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="d61e3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d61e3-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="d61e3-115">Görev tabanlı zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="d61e3-115">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
