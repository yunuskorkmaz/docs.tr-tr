---
title: 'Nasıl Yapılır: Alt Görevin Üst Göreve Eklenmesini Önleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
ms.openlocfilehash: 265b6d06f17a1dfbee3f009feff1ee1645e62a46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139254"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Nasıl Yapılır: Alt Görevin Üst Göreve Eklenmesini Önleme
Bu belgede, bir alt görevin üst göreve iliştirilmesi nasıl önleneceği gösterilmektedir. Bir alt görevin kendi üst öğesine iliştirmesini önlemek, üçüncü taraf tarafından yazılan ve ayrıca görevleri kullanan bir bileşeni çağırdığınızda yararlıdır. Örneğin, bir <xref:System.Threading.Tasks.Task> veya <xref:System.Threading.Tasks.Task%601> nesnesi oluşturmak için <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> seçeneğini kullanan bir üçüncü taraf bileşeni, uzun süre çalışan veya işlenmemiş bir özel durum oluşturursa kodunuzda sorunlara neden olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, varsayılan seçenekleri kullanmanın etkilerini, alt görevin üst öğeye iliştirmesini engellemeye yönelik etkileri ile karşılaştırır. Örnek, bir <xref:System.Threading.Tasks.Task> nesnesi kullanan bir üçüncü taraf kitaplığına çağıran bir <xref:System.Threading.Tasks.Task> nesnesi oluşturur. Üçüncü taraf kitaplığı, <xref:System.Threading.Tasks.Task> nesnesini oluşturmak için <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> seçeneğini kullanır. Uygulama, üst görevi oluşturmak için <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneğini kullanır. Bu seçenek çalışma zamanına, alt görevlerdeki <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> belirtimini kaldırmasını söyler.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Bir üst görev tüm alt görevler tamamlanana kadar bitmediğinden, uzun süreli bir alt görev genel uygulamanın kötü bir şekilde çalışmasına neden olabilir. Bu örnekte, uygulama ana görevi oluşturmak için varsayılan seçenekleri kullandığında, üst görev tamamlanmadan önce alt görevin son olması gerekir. Uygulama <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> seçeneğini kullandığında, alt öğe üst öğeye eklenmez. Bu nedenle, uygulama, üst görev bittikten sonra ve alt görevin bitmesini beklemek zorunda olduktan sonra ek iş gerçekleştirebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
