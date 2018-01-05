---
title: "Nasıl yapılır: Bir Görevden Değer Döndürme"
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
helpviewer_keywords: tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4497f7f9c6802a9b3d4edca66ceb4a894a59646a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="6bb85-102">Nasıl yapılır: Bir Görevden Değer Döndürme</span><span class="sxs-lookup"><span data-stu-id="6bb85-102">How to: Return a Value from a Task</span></span>
<span data-ttu-id="6bb85-103">Bu örnek, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> özelliğinden bir değer döndürmek için <xref:System.Threading.Tasks.Task%601.Result%2A> türünün nasıl kullanıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6bb85-103">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="6bb85-104">C:\Users\Public\Pictures\Sample Pictures\ dizinin olmasını ve dosya içermesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="6bb85-104">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bb85-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="6bb85-105">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="6bb85-106"><xref:System.Threading.Tasks.Task%601.Result%2A> özelliği, görev bitene kadar çağıran iş parçacığını engeller.</span><span class="sxs-lookup"><span data-stu-id="6bb85-106">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="6bb85-107">Bir sonuç geçirmek nasıl görmek için <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> devamlılık görevi için bkz: [zincirleme görevleri devamlılık görevlerini kullanarak tarafından](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="6bb85-107">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb85-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6bb85-108">See Also</span></span>  
 [<span data-ttu-id="6bb85-109">Görev Tabanlı Zaman Uyumsuz Desen</span><span class="sxs-lookup"><span data-stu-id="6bb85-109">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)  
 [<span data-ttu-id="6bb85-110">PLINQ ve TPL'deki Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="6bb85-110">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
