---
description: 'Daha fazla bilgi edinin: nasıl yapılır: paralel görevlerle Ikili ağacı çapraz geçiş'
title: 'Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
ms.openlocfilehash: f6b053bb9b480e85698dcd098a750d38d2ef403a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99629545"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="acb63-103">Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme</span><span class="sxs-lookup"><span data-stu-id="acb63-103">How to: Traverse a Binary Tree with Parallel Tasks</span></span>

<span data-ttu-id="acb63-104">Aşağıdaki örnekte, bir ağaç veri yapısına çapraz geçiş yapmak için paralel görevlerin kullanılabileceği iki yol gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="acb63-104">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="acb63-105">Ağacın kendisi bir alıştırma olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="acb63-105">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acb63-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="acb63-106">Example</span></span>  

 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="acb63-107">Gösterilen iki yöntem işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="acb63-107">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="acb63-108"><xref:System.Threading.Tasks.TaskFactory.StartNew%2A>Görevleri oluşturmak ve çalıştırmak için yöntemini kullanarak, görevleri beklemek ve özel durumları işlemek için kullanılabilecek görevlerden geri bir tanıtıcı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="acb63-108">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acb63-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acb63-109">See also</span></span>

- [<span data-ttu-id="acb63-110">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="acb63-110">Task Parallel Library (TPL)</span></span>](task-parallel-library-tpl.md)
