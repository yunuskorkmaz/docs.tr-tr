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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196653"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="64e85-102">Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme</span><span class="sxs-lookup"><span data-stu-id="64e85-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="64e85-103">Aşağıdaki örnek, bir ağaç veri yapısı geçirmek için Paralel Görevler, kullanılabilir iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="64e85-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="64e85-104">Ağaç oluşturulmasını bir alıştırma olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="64e85-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64e85-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="64e85-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="64e85-106">Gösterilen iki yöntem işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="64e85-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="64e85-107">Kullanarak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> yöntemi oluşturmak ve görevleri çalıştırmak için bir tanıtıcı görevlerde bekleyen ve özel durumları işlemek için kullanılan görevler geri alın.</span><span class="sxs-lookup"><span data-stu-id="64e85-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64e85-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64e85-108">See also</span></span>

- [<span data-ttu-id="64e85-109">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="64e85-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
