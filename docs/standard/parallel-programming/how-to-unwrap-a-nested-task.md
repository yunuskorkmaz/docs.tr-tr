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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 224f9273b0c8c9445a6a9e25f064e9726acc84f0
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44707756"
---
# <a name="how-to-unwrap-a-nested-task"></a>Nasıl yapılır: İç İçe Geçmiş Bir Görevi Sarmalamadan Çıkarma
Bir yöntemi, bir görev döndürür ve ardından bekleyebilir veya bu görevi, aşağıdaki örnekte gösterildiği gibi devam eder:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 Önceki örnekte, <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği türüdür `string` (`String` Visual Basic'te).  
  
 Ancak, bazı senaryolarda, bir görevi başka bir görev oluşturun ve sonra iç içe görev dönmek isteyebilirsiniz. Bu durumda, `TResult` kapsayan görevin kendisi bir görevdir. Aşağıdaki örnekte, sonuç özelliktir bir `Task<Task<string>>` C# veya `Task(Of Task(Of String))` Visual Basic'te.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Dış bir görevi sarmalamadan çıkarma ve özgün görevi almak için kod yazmayı mümkün olsa da ve kendi <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği bu tür kod özel durumlar ve ayrıca iptal isteklerini işlemesi gerekir çünkü kolay değildir. Bu durumda, aşağıdakilerden birini kullanmanızı öneririz <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> genişletme yöntemleri, aşağıdaki örnekte gösterildiği gibi.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Yöntemleri herhangi dönüştürmek için kullanılabilir `Task<Task>` veya `Task<Task<TResult>>` (`Task(Of Task)` veya `Task(Of Task(Of TResult))` Visual Basic'te) için bir `Task` veya `Task<TResult>` (`Task(Of TResult)` Visual Basic'te). Yeni görevin tam olarak iç iç içe geçmiş görev temsil eder ve iptal durumunu ve tüm özel durumları içerir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> genişletme yöntemleri.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
- [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
