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
ms.openlocfilehash: 5ac81a61691ec20daafc9e18978ba5814a150383
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288075"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="bdcec-102">Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme</span><span class="sxs-lookup"><span data-stu-id="bdcec-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="bdcec-103">Aşağıdaki örnekte, bir ağaç veri yapısına çapraz geçiş yapmak için paralel görevlerin kullanılabileceği iki yol gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bdcec-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="bdcec-104">Ağacın kendisi bir alıştırma olarak kalır.</span><span class="sxs-lookup"><span data-stu-id="bdcec-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdcec-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdcec-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="bdcec-106">Gösterilen iki yöntem işlevsel olarak eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="bdcec-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="bdcec-107"><xref:System.Threading.Tasks.TaskFactory.StartNew%2A>Görevleri oluşturmak ve çalıştırmak için yöntemini kullanarak, görevleri beklemek ve özel durumları işlemek için kullanılabilecek görevlerden geri bir tanıtıcı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="bdcec-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdcec-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdcec-108">See also</span></span>

- [<span data-ttu-id="bdcec-109">Görev Paralel Kitaplığı (TPL)</span><span class="sxs-lookup"><span data-stu-id="bdcec-109">Task Parallel Library (TPL)</span></span>](task-parallel-library-tpl.md)
