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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4287879bd95f7bc1e1dc99f74fa0d7cc0fe737f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191033"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Nasıl yapılır: Bir Görevde EAP Desenlerini Sarmalama
Aşağıdaki örnek, rastgele bir olay tabanlı zaman uyumsuz desen (EAP) işlem dizisi bir görev olarak kullanarak nasıl sunacağınızı öğrenin gösterir bir <xref:System.Threading.Tasks.TaskCompletionSource%601>. Örnek ayrıca nasıl kullanılacağını gösterir bir <xref:System.Threading.CancellationToken> üzerinde yerleşik iptal yöntemleri çağırmak için <xref:System.Net.WebClient> nesneleri.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TPL ve Geleneksel .NET Framework Zaman Uyumsuz Programlama](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
