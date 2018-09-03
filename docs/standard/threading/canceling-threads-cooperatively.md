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
ms.openlocfilehash: 24cacf0323c96f6959442dea94b0540633661bce
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485605"
---
# <a name="canceling-threads-cooperatively"></a>İş parçacıklarını işbirliği ile iptal etme

Önce .NET Framework 4 ve .NET Framework, başlatıldıktan sonra bir iş parçacığı işbirliği içerisinde devamlılığı iptal etmek için yerleşik bir yolu yoktur sağlanır. Ancak, .NET Framework 4 ile başlayarak, kullanabileceğiniz bir <xref:System.Threading.CancellationToken?displayProperty=nameWithType> yalnızca bunları iptal etmek için kullanabileceğiniz gibi iş parçacıkları, iptal etmek için <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya PLINQ sorguları. Ancak <xref:System.Threading.Thread?displayProperty=nameWithType> sınıfı iptal belirteçleri için yerleşik destek sunmaz, bir iş parçacığı yordamı için bir belirteç kullanarak geçirebilirsiniz <xref:System.Threading.Thread> alan oluşturucu bir <xref:System.Threading.ParameterizedThreadStart> temsilci. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

 [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](using-threads-and-threading.md)  
