---
title: 'Nasıl yapılır: Bir Görevde EAP Desenlerini Sarmalama'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: ac7436892c644340286bb4670bf75c9cd63a8ce5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106817"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Nasıl yapılır: Bir Görevde EAP Desenlerini Sarmalama
Aşağıdaki örnek, bir <xref:System.Threading.Tasks.TaskCompletionSource%601>kullanarak bir görev olarak rastgele bir olay tabanlı zaman uyumsuz model (EAP) işlemleri dizisinin nasıl gösterileceğini gösterir. Örnek ayrıca, <xref:System.Net.WebClient> nesnelerinde yerleşik iptal yöntemlerini çağırmak için bir <xref:System.Threading.CancellationToken> nasıl kullanacağınızı gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TPL ve Geleneksel .NET Framework Zaman Uyumsuz Programlama](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
