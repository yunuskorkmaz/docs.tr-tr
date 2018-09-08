---
title: İş parçacıklarını işbirliği ile iptal etme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd32deb9c8719a12b76aaea8ec91a17471cf18f9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221499"
---
# <a name="canceling-threads-cooperatively"></a>İş parçacıklarını işbirliği ile iptal etme

Önce .NET Framework 4 ve .NET Framework, başlatıldıktan sonra bir iş parçacığı işbirliği içerisinde devamlılığı iptal etmek için yerleşik bir yolu yoktur sağlanır. Ancak, .NET Framework 4 ile başlayarak, kullanabileceğiniz bir <xref:System.Threading.CancellationToken?displayProperty=nameWithType> yalnızca bunları iptal etmek için kullanabileceğiniz gibi iş parçacıkları, iptal etmek için <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya PLINQ sorguları. Ancak <xref:System.Threading.Thread?displayProperty=nameWithType> sınıfı iptal belirteçleri için yerleşik destek sunmaz, bir iş parçacığı yordamı için bir belirteç kullanarak geçirebilirsiniz <xref:System.Threading.Thread> alan oluşturucu bir <xref:System.Threading.ParameterizedThreadStart> temsilci. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](using-threads-and-threading.md)
