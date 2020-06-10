---
title: 'Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme'
description: .NET 'teki bir görevi ve alt öğelerini iptal etme örneklerine bakın. Örnekler, iptal edilebilir görev oluşturma işleminden, görevin iptal edildiğini fark eden adımları kapsar.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: 66daf00680b65aace1ce6367761e3ed81596d33b
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662686"
---
# <a name="how-to-cancel-a-task-and-its-children"></a>Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme
Bu örnekler, aşağıdaki görevlerin nasıl gerçekleştirildiğini gösterir:  
  
1. İptal edilebilen bir görevi oluşturmak ve başlatmak.  
  
2. Kullanıcı temsilcinize ve isteğe bağlı olarak görev örneğine bir iptal belirteci geçirmek.  
  
3. Kullanıcı temsilcinizde iptal belirtecini fark etmek ve buna yanıt vermek.  
  
4. İsteğe bağlı olarak, çağıran iş parçacığında görevin iptal edildiğini belirlemek.  
  
 Çağıran iş parçacığı görevi zorla bitirmez; yalnızca iptalin istendiğini bildirir. Görev zaten çalışıyorsa, isteği fark etmek ve uygun bir şekilde karşılık vermek kullanıcı temsilcisinin görevidir. Görev çalışmadan iptal istenirse, kullanıcı temsilcisi asla yürütülmez ve görev nesnesi Canceled durumuna geçer.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir iptal isteğine yanıt olarak bir <xref:System.Threading.Tasks.Task> öğesinin ve alt öğelerinin nasıl sonlandırıldığını gösterir. Ayrıca, kullanıcı temsilcisi bir <xref:System.Threading.Tasks.TaskCanceledException> oluşturarak sonlandırdığında, çağıran iş parçacığının, isteğe bağlı olarak, görevlerin bitmesini beklemek için <xref:System.Threading.Tasks.Task.Wait%2A> yöntemini veya <xref:System.Threading.Tasks.Task.WaitAll%2A> yöntemini kullanabileceğini de gösterir. Bu durumda, özel durumları işlemek için çağıran iş parçacığında bir `try/catch` bloğu kullanmanız gerekir.  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> sınıfı, <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> ve <xref:System.Threading.CancellationToken?displayProperty=nameWithType> türlerini temel alan iptal modeliyle tamamen tümleşiktir. Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında iptal](../threading/cancellation-in-managed-threads.md) ve [Görev iptali](task-cancellation.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [Görev tabanlı zaman uyumsuz programlama](task-based-asynchronous-programming.md)
- [Eklenen ve Ayrılan Alt Görevler](attached-and-detached-child-tasks.md)
- [PLıNQ ve TPL 'deki lambda Ifadeleri](lambda-expressions-in-plinq-and-tpl.md)
