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
ms.openlocfilehash: b79337e6ee8057506ff87c696cecd6b038eeebfc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141647"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme
Aşağıdaki örnekte, bir ağaç veri yapısına çapraz geçiş yapmak için paralel görevlerin kullanılabileceği iki yol gösterilmektedir. Ağacın kendisi bir alıştırma olarak kalır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Gösterilen iki yöntem işlevsel olarak eşdeğerdir. Görevleri oluşturmak ve çalıştırmak için <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> yöntemini kullanarak, görevleri beklemek ve özel durumları işlemek için kullanılabilecek görevlerden geri bir tanıtıcı alırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
