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
ms.openlocfilehash: d6446145d34d22503697bbca59bc2cb2cd2619cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580370"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Nasıl yapılır: Paralel Görevler İçeren Bir İkili Ağacı Gezme
Aşağıdaki örnek Paralel Görevler bir ağaç veri yapısı geçiş yapmak için kullanılabilecek iki yolunu gösterir. Ağaç oluşturulmasını bir alıştırma olarak kalır.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Gösterilen iki yöntem işlevsel olarak eşdeğerdir. Kullanarak <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> yöntemi oluşturmak ve görevleri çalıştırmak için bir tanıtıcı görevlerde bekleyin ve özel durumları işlemek için kullanılan görevler geri alın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Paralel Kitaplığı (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
