---
title: 'Nasıl yapılır: Bir Görevden Değer Döndürme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: 495f68114bfe960b8182be4ab76b72043b2d0cc7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141663"
---
# <a name="how-to-return-a-value-from-a-task"></a>Nasıl yapılır: Bir Görevden Değer Döndürme
Bu örnek, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> özelliğinden bir değer döndürmek için <xref:System.Threading.Tasks.Task%601.Result%2A> türünün nasıl kullanıldığını gösterir. C:\Users\Public\Pictures\Sample Pictures\ dizinin olmasını ve dosya içermesini gerektirir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği, görev bitene kadar çağıran iş parçacığını engeller.  
  
 Bir <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> sonucunu bir devamlılık görevine geçirme hakkında bilgi için bkz. [devamlılık görevlerini kullanarak görevleri zincirleme](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev Tabanlı Zaman Uyumsuz Desen](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
