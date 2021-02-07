---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: Iç Içe bir görevi sarmalama'
title: 'Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: 0b9380d82e2b61fe371cfe56a849403212853074
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701696"
---
# <a name="how-to-unwrap-a-nested-task"></a>Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma

Aşağıdaki örnekte gösterildiği gibi, bir yöntemden bir görev döndürebilir ve sonra bu görevden bekleyebilir veya devam edebilirsiniz:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 Önceki örnekte, <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği türündedir `string` ( `String` Visual Basic).  
  
 Ancak, bazı senaryolarda başka bir görevde bir görev oluşturmak ve ardından iç içe görevi döndürmek isteyebilirsiniz. Bu durumda, `TResult` kapsayan görevin kendisi bir görevdir. Aşağıdaki örnekte Result özelliği `Task<Task<string>>` C# dilinde veya `Task(Of Task(Of String))` Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Dış görevin sarmalaması geri almak ve özgün görevi ve özelliğini almak üzere kod yazmak mümkün olsa da <xref:System.Threading.Tasks.Task%601.Result%2A> , özel durumları ve iptal isteklerini işlemeniz gerektiğinden, bu tür kodun yazılması kolay değildir. Bu durumda, <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Aşağıdaki örnekte gösterildiği gibi, uzantı yöntemlerinden birini kullanmanızı öneririz.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 Yöntemler, veya <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> `Task<Task>` `Task<Task<TResult>>` ( `Task(Of Task)` `Task(Of Task(Of TResult))` Visual Basic) bir veya ' a ( `Task` `Task<TResult>` `Task(Of TResult)` Visual Basic) dönüştürmek için kullanılabilir. Yeni görev iç iç içe görevi tamamen temsil eder ve iptal durumu ve tüm özel durumları içerir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, genişletme yöntemlerinin nasıl kullanılacağını göstermektedir <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> .  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Görev tabanlı zaman uyumsuz programlama](task-based-asynchronous-programming.md)
