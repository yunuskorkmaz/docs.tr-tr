---
title: "Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma"
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
helpviewer_keywords: tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2da3de912abb693c4342e1ede02f273348e4b571
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-unwrap-a-nested-task"></a>Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma
Bir yöntemi, bir görev döndürür ve ardından beklemesi veya bu görevi, aşağıdaki örnekte gösterildiği gibi devam edebilirsiniz:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 Önceki örnekte, <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği türüdür `string` (`String` Visual Basic'te).  
  
 Ancak, bazı senaryolarda, başka bir görev içinde bir görev oluşturmak ve iç içe geçmiş görev dönmek isteyebilirsiniz. Bu durumda, `TResult` kapsayan görevin kendisi bir görevdir. Aşağıdaki örnekte, sonuç özelliği olan bir `Task<Task<string>>` C# veya `Task(Of Task(Of String))` Visual Basic'te.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Dış bir görevi sarmalamadan çıkarma ve özgün görev almak için kod yazmayı mümkün olsa ve kendi <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği, bu tür kodu özel durumlar ve aynı zamanda iptal isteklerini işlemesi gerekir çünkü yazmak kolay değildir. Bu durumda, aşağıdakilerden birini kullanmanızı öneririz <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> aşağıdaki örnekte gösterildiği gibi genişletme yöntemleri.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Yöntemleri, herhangi bir dönüştürme için kullanılabilir `Task<Task>` veya `Task<Task<TResult>>` (`Task(Of Task)` veya `Task(Of Task(Of TResult))` Visual Basic'te) için bir `Task` veya `Task<TResult>` (`Task(Of TResult)` Visual Basic'te). Yeni görev tam olarak iç içe geçmiş bir görevi temsil eder ve iptal durumunu ve tüm özel durumları içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl kullanılacağı ortaya <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> genişletme yöntemleri.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [Görev tabanlı zaman uyumsuz programlama](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
