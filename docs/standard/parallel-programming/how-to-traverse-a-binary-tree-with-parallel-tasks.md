---
title: 'Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
ms.openlocfilehash: ca70021c7d071abe480cb4ed866e34f171cc3b45
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825539"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme
Aşağıdaki örnekte, bir ağaç veri yapısına çapraz geçiş yapmak için paralel görevlerin kullanılabileceği iki yol gösterilmektedir. Ağacın kendisi bir alıştırma olarak kalır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Gösterilen iki yöntem işlevsel olarak eşdeğerdir. <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>Görevleri oluşturmak ve çalıştırmak için yöntemini kullanarak, görevleri beklemek ve özel durumları işlemek için kullanılabilecek görevlerden geri bir tanıtıcı alırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](task-parallel-library-tpl.md)
