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
ms.openlocfilehash: 36de18e976401dd0cde878852c064aa982b8acde
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188503"
---
# <a name="canceling-threads-cooperatively"></a>İş parçacıklarını işbirliği ile iptal etme

.NET Framework 4 ' ten önce, .NET, başlatıldıktan sonra bir iş parçacığını iptal etmek için yerleşik bir yöntem sağlamamıştı. Ancak, .NET Framework 4 ' ü kullanmaya başlayarak, <xref:System.Threading.CancellationToken?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya PLINQ sorgularını iptal etmek için bunları kullanabileceğiniz gibi, iş parçacıklarını iptal etmek için kullanabilirsiniz. Sınıfı, <xref:System.Threading.Thread?displayProperty=nameWithType> iptal belirteçleri için yerleşik destek sunmasa da, bir <xref:System.Threading.Thread> temsilciyi alan oluşturucuyu kullanarak bir iş parçacığı yordamına belirteç geçirebilirsiniz <xref:System.Threading.ParameterizedThreadStart> . Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Iş parçacıkları ve Iş parçacığı kullanma](using-threads-and-threading.md)
