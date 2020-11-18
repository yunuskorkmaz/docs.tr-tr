---
title: 'Nasıl yapılır: Bir Görevde EAP Desenlerini Sarmalama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
ms.openlocfilehash: 2d6788634fe03bed7a380184c0e954954e224aec
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826690"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Nasıl yapılır: Bir Görevde EAP Desenlerini Sarmalama
Aşağıdaki örnek, bir kullanarak Event-Based zaman uyumsuz model (EAP) işlemlerini bir görev olarak ortaya çıkarmak gösterilmektedir <xref:System.Threading.Tasks.TaskCompletionSource%601> . Örnek ayrıca, <xref:System.Threading.CancellationToken> nesneleri üzerinde yerleşik iptal yöntemlerini çağırmak için nasıl kullanılacağını gösterir <xref:System.Net.WebClient> .  
  
## <a name="example"></a>Örnek  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TPL ve Geleneksel .NET Zaman Uyumsuz Programlama](tpl-and-traditional-async-programming.md)
