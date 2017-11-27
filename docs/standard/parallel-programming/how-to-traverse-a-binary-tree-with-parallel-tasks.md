---
title: "Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme"
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
helpviewer_keywords: tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c029a763faaa0b4d6ea5612efe079e47415b6fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="f6f71-102">Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme</span><span class="sxs-lookup"><span data-stu-id="f6f71-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="f6f71-103">Aşağıdaki örnek Paralel Görevler bir ağaç veri yapısı geçiş yapmak için kullanılabilecek iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6f71-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="f6f71-104">Ağaç oluşturulmasını bir alıştırma olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="f6f71-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6f71-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6f71-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="f6f71-106">Gösterilen iki yöntem işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="f6f71-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="f6f71-107">Kullanarak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> yöntemi oluşturmak ve görevleri çalıştırmak için bir tanıtıcı görevlerde bekleyin ve özel durumları işlemek için kullanılan görevler geri alın.</span><span class="sxs-lookup"><span data-stu-id="f6f71-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6f71-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6f71-108">See Also</span></span>  
 [<span data-ttu-id="f6f71-109">Görev paralel kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="f6f71-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
