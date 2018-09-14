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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 224f9273b0c8c9445a6a9e25f064e9726acc84f0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45526960"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="03abc-102">Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma</span><span class="sxs-lookup"><span data-stu-id="03abc-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="03abc-103">Bir yöntemi, bir görev döndürür ve ardından bekleyebilir veya bu görevi, aşağıdaki örnekte gösterildiği gibi devam eder:</span><span class="sxs-lookup"><span data-stu-id="03abc-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="03abc-104">Önceki örnekte, <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği türüdür `string` (`String` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="03abc-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="03abc-105">Ancak, bazı senaryolarda, bir görevi başka bir görev oluşturun ve sonra iç içe görev dönmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="03abc-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="03abc-106">Bu durumda, `TResult` kapsayan görevin kendisi bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="03abc-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="03abc-107">Aşağıdaki örnekte, sonuç özelliktir bir `Task<Task<string>>` C# veya `Task(Of Task(Of String))` Visual Basic'te.</span><span class="sxs-lookup"><span data-stu-id="03abc-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="03abc-108">Dış bir görevi sarmalamadan çıkarma ve özgün görevi almak için kod yazmayı mümkün olsa da ve kendi <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği bu tür kod özel durumlar ve ayrıca iptal isteklerini işlemesi gerekir çünkü kolay değildir.</span><span class="sxs-lookup"><span data-stu-id="03abc-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="03abc-109">Bu durumda, aşağıdakilerden birini kullanmanızı öneririz <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> genişletme yöntemleri, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="03abc-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="03abc-110"><xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Yöntemleri herhangi dönüştürmek için kullanılabilir `Task<Task>` veya `Task<Task<TResult>>` (`Task(Of Task)` veya `Task(Of Task(Of TResult))` Visual Basic'te) için bir `Task` veya `Task<TResult>` (`Task(Of TResult)` Visual Basic'te).</span><span class="sxs-lookup"><span data-stu-id="03abc-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="03abc-111">Yeni görevin tam olarak iç iç içe geçmiş görev temsil eder ve iptal durumunu ve tüm özel durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="03abc-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03abc-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="03abc-112">Example</span></span>  
 <span data-ttu-id="03abc-113">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> genişletme yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="03abc-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="03abc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="03abc-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
- [<span data-ttu-id="03abc-115">Görev Tabanlı Zaman Uyumsuz Desen</span><span class="sxs-lookup"><span data-stu-id="03abc-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
