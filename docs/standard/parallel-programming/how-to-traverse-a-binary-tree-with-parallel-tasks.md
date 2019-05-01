---
title: 'Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fd937d6ce2edf0c47fce78d48a90ec1aa409eef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797156"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="b4ac5-102">Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme</span><span class="sxs-lookup"><span data-stu-id="b4ac5-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="b4ac5-103">Aşağıdaki örnek, bir ağaç veri yapısı geçirmek için Paralel Görevler, kullanılabilir iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4ac5-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="b4ac5-104">Ağaç oluşturulmasını bir alıştırma olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="b4ac5-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4ac5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4ac5-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="b4ac5-106">Gösterilen iki yöntem işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b4ac5-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="b4ac5-107">Kullanarak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> yöntemi oluşturmak ve görevleri çalıştırmak için bir tanıtıcı görevlerde bekleyen ve özel durumları işlemek için kullanılan görevler geri alın.</span><span class="sxs-lookup"><span data-stu-id="b4ac5-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ac5-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4ac5-108">See also</span></span>

- [<span data-ttu-id="b4ac5-109">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="b4ac5-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
