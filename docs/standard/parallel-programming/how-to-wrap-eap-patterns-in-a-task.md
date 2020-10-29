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
ms.openlocfilehash: 339544ce9f0ee44097d1a60e0d2c2035d81f674d
ms.sourcegitcommit: 6d09ae36acba0b0e2ba47999f8f1a725795462a2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92925369"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Nasıl yapılır: Bir Görevde EAP Desenlerini Sarmalama
Aşağıdaki örnek, bir kullanarak Event-Based zaman uyumsuz model (EAP) işlemlerini bir görev olarak ortaya çıkarmak gösterilmektedir <xref:System.Threading.Tasks.TaskCompletionSource%601> . Örnek ayrıca, <xref:System.Threading.CancellationToken> nesneleri üzerinde yerleşik iptal yöntemlerini çağırmak için nasıl kullanılacağını gösterir <xref:System.Net.WebClient> .  
  
## <a name="example"></a>Örnek  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TPL ve geleneksel .NET zaman uyumsuz programlama](tpl-and-traditional-async-programming.md)
