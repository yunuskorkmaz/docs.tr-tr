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
ms.openlocfilehash: 144d004d697b84a011cedafc7d07b679ef8852c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288153"
---
# <a name="how-to-return-a-value-from-a-task"></a>Nasıl yapılır: Bir Görevden Değer Döndürme
Bu örnek, <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> özelliğinden bir değer döndürmek için <xref:System.Threading.Tasks.Task%601.Result%2A> türünün nasıl kullanıldığını gösterir. C:\Users\Public\Pictures\Sample Pictures\ dizinin olmasını ve dosya içermesini gerektirir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <xref:System.Threading.Tasks.Task%601.Result%2A> özelliği, görev bitene kadar çağıran iş parçacığını engeller.  
  
 Bir devamlılık görevinin sonucunu nasıl geçitirsiniz görmek için <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> bkz. [devamlılık görevlerini kullanarak görevleri zincirleme](chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Görev tabanlı zaman uyumsuz programlama](task-based-asynchronous-programming.md)
- [PLıNQ ve TPL 'deki lambda Ifadeleri](lambda-expressions-in-plinq-and-tpl.md)
