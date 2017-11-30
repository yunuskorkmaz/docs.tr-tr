---
title: "İş Parçacıklarını İşbirliği ile İptal Etme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 482f48b347af1a4f76231abcb15abc2f4dba168b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="canceling-threads-cooperatively"></a>İş Parçacıklarını İşbirliği ile İptal Etme
Öncesinde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework sağlanan başlatıldığından sonra bir iş parçacığı işbirliği ile iptal yerleşik mümkün değildir. Bununla birlikte, [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], yalnızca bunları iptal etmek için kullanabileceğiniz gibi iş parçacıkları, iptal etmek için İptal belirteçlerini kullanabilirsiniz <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya PLINQ sorgular. Ancak <xref:System.Threading.Thread?displayProperty=nameWithType> sınıfı iptal belirteçlerini için yerleşik destek sunar değil, bir iş parçacığı yordamı için bir belirteç kullanarak geçirebilirsiniz <xref:System.Threading.Thread> alan oluşturucu bir <xref:System.Threading.ParameterizedThreadStart> temsilci. Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş parçacığı kullanma ve iş parçacığı oluşturma](../../../docs/standard/threading/using-threads-and-threading.md)
