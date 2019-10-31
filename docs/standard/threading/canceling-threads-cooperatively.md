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
ms.openlocfilehash: 1d1433ecf39974bf9e68fe07b9d0818ac16fb544
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138123"
---
# <a name="canceling-threads-cooperatively"></a>İş parçacıklarını işbirliği ile iptal etme

.NET Framework 4 ' ten önce, .NET Framework başlatıldıktan sonra bir iş parçacığını iptal etmek için yerleşik bir yöntem sağlanmadı. Ancak, .NET Framework 4 ' ü kullanmaya başlayarak, nesneleri <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya PLıNQ sorgularını iptal etmek için kullanabileceğiniz gibi, iş parçacıklarını iptal etmek için bir <xref:System.Threading.CancellationToken?displayProperty=nameWithType> kullanabilirsiniz. <xref:System.Threading.Thread?displayProperty=nameWithType> sınıfı, iptal belirteçleri için yerleşik destek sunmaz, ancak bir <xref:System.Threading.ParameterizedThreadStart> temsilcisi alan <xref:System.Threading.Thread> oluşturucusunu kullanarak bir iş parçacığı yordamına belirteç geçirebilirsiniz. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma](using-threads-and-threading.md)
