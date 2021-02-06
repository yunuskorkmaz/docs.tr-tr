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
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme

Aşağıdaki örnekte, bir ağaç veri yapısına çapraz geçiş yapmak için paralel görevlerin kullanılabileceği iki yol gösterilmektedir. Ağacın kendisi bir alıştırma olarak kalır.  
  
## <a name="example"></a>Örnek  

 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Gösterilen iki yöntem işlevsel olarak eşdeğerdir. <xref:System.Threading.Tasks.TaskFactory.StartNew%2A>Görevleri oluşturmak ve çalıştırmak için yöntemini kullanarak, görevleri beklemek ve özel durumları işlemek için kullanılabilecek görevlerden geri bir tanıtıcı alırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](task-parallel-library-tpl.md)
