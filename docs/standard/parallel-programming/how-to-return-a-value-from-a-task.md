---
title: 'Nasıl yapılır: Bir Görevden Değer Döndürme'
description: <TResult>.Net 'Teki Result özelliğinden bir değer döndürmek Için System. Threading. Tasks. Task türünü nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: c7a4a683545c9ef0448d9cdce769aae79215aecf
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825617"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="e8815-103">Nasıl yapılır: Bir Görevden Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="e8815-103">How to: Return a Value from a Task</span></span>
<span data-ttu-id="e8815-104">Bu örnek, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> özelliğinden bir değer döndürmek için <xref:System.Threading.Tasks.Task%601.Result%2A> türünün nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8815-104">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="e8815-105">C:\Users\Public\Pictures\Sample Pictures\ dizinin olmasını ve dosya içermesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e8815-105">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8815-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e8815-106">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="e8815-107"><xref:System.Threading.Tasks.Task%601.Result%2A> özelliği, görev bitene kadar çağıran iş parçacığını engeller.</span><span class="sxs-lookup"><span data-stu-id="e8815-107">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="e8815-108">Bir devamlılık görevinin sonucunu nasıl geçitirsiniz görmek için <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> bkz. [devamlılık görevlerini kullanarak görevleri zincirleme](chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="e8815-108">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8815-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8815-109">See also</span></span>

- [<span data-ttu-id="e8815-110">Görev tabanlı zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="e8815-110">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="e8815-111">PLıNQ ve TPL 'deki lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="e8815-111">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
