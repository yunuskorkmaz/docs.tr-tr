---
title: 'Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: c72654a2bc21035fe706d76018bb163d8ba01ee8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106901"
---
# <a name="how-to-unwrap-a-nested-task"></a>Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma
Bir görevi bir yöntemden döndürebilir ve aşağıdaki örnekte gösterildiği gibi bu görevi bekleyebilir veya bu görevden devam edebilirsiniz:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 Önceki örnekte, <xref:System.Threading.Tasks.Task%601.Result%2A> özellik tür `string` (Visual`String` Basic' de).  
  
 Ancak, bazı senaryolarda, başka bir görev içinde bir görev oluşturmak ve sonra iç içe görev dönmek isteyebilirsiniz. Bu durumda, `TResult` çevreleyen görevin kendisi bir görevdir. Aşağıdaki örnekte, Sonuç özelliği `Task<Task<string>>` C#'da `Task(Of Task(Of String))` veya Visual Basic'te dir.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Dış görevin paketlerini açmak ve özgün görevi ve özelliğini <xref:System.Threading.Tasks.Task%601.Result%2A> almak için kod yazmak mümkün olsa da, özel durumları ve ayrıca iptal isteklerini işlemeniz gerektiğinden bu kodu yazmak kolay değildir. Bu durumda, aşağıdaki örnekte gösterildiği <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> gibi uzantı yöntemlerinden birini kullanmanızı öneririz.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 Bu <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> yöntemler, herhangi bir `Task<Task>` `Task<Task<TResult>>` veya`Task(Of Task)` `Task(Of Task(Of TResult))` (veya Visual Basic'te) bir `Task` veya `Task<TResult>` (Visual`Task(Of TResult)` Basic) dönüştürmek için kullanılabilir. Yeni görev iç içe geçme görevini tam olarak temsil eder ve iptal durumunu ve tüm özel durumları içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, uzantı yöntemlerinin nasıl kullanılacağını <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> göstermektedir.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
