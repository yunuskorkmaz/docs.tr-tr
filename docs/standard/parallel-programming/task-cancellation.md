---
title: "Görev iptali"
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
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 106c89ca9fcfb8bbab23b982cdc524ff78d21d15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="task-cancellation"></a>Görev iptali
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> sınıfları, .NET Framework'teki iptal belirteçlerini kullanımı ile iptal destekler. Daha fazla bilgi için bkz: [yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md). Görev sınıflarında iptal etme, iptal edilebilir bir işlemi temsil eden kullanıcı temsilcisiyle iptal etmeyi isteyen kod arasında yapılan bir işbirliğini içerir.  İstekte bulunan kod arama başarılı iptal içerir <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemi ve kullanıcı temsilci zamanında işlemi sonlandırılıyor. Aşağıdaki seçeneklerden birini kullanarak işlemi sonlandırabilirsiniz:  
  
-   Yalnızca temsilciden döndürerek. Birçok senaryoda bu yeterlidir; Ancak, bu şekilde iptal bir görev örneği için geçiş <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> durum değil <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> durumu.  
  
-   Atma tarafından bir <xref:System.OperationCanceledException> ve onu belirtecin iptal istendi. Bunu yapmak için tercih edilen yol <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> yöntemi. Bu şekilde iptal edilen bir görev, çağıran kodun iptal isteğine yanıt olarak verilen görevi doğrulamak için kullanabileceği İptal Edildi durumuna geçer.  
  
 Aşağıdaki örnekte, özel durum oluşturan görev iptal işlemi için temel düzen gösterilmektedir. Belirtecin kullanıcı temsilcisine ve görev örneğine geçirildiğini unutmayın.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Daha eksiksiz bir örnek için bkz: [nasıl yapılır: bir görevi ve ait alt öğelerini iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Ne zaman bir görev örneği uyan bir <xref:System.OperationCanceledException> kullanıcı kodu tarafından oluşturulan, özel durumun belirteci kendi ilişkili belirtecine (görev oluşturulan API için geçirilen bir) karşılaştırır. Aynı ve belirtecin olmaları durumunda <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği true döndürür, görev bunu iptal aktarımının olarak yorumlar ve iptal edildi durumuna geçiş yapar. Kullanmıyorsanız, bir <xref:System.Threading.Tasks.Task.Wait%2A> veya <xref:System.Threading.Tasks.Task.WaitAll%2A> görevi yalnızca durumunu ayarlar sonra görevin tamamlanmasını bekle yöntemi <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 İptal edildi durumuna geçiş bir görevde bekliyorsa bir <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> özel durumu (sarmalanmış bir <xref:System.AggregateException> özel durum) oluşturulur. Bu özel durumun, hatalı bir durum yerine başarılı bir iptal işlemini gösterdiğine dikkat edin. Bu nedenle, görevin <xref:System.Threading.Tasks.Task.Exception%2A> özelliği döndürür `null`.  
  
 Belirtecin <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği false döndürür veya özel durumun belirteci eşleşmiyorsa görev belirteç, <xref:System.OperationCanceledException> Faulted durumuna geçiş görevi neden normal bir özel durum gibi işlem görür. Ayrıca, başka özel durumların da Görevin Hatalı durumuna geçmesine neden olacağını unutmayın. Tamamlanan görevin durumunu alma <xref:System.Threading.Tasks.Task.Status%2A> özelliği.  
  
 İptal işlemi istendikten sonra görev bazı öğeleri işlemeye devam edebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 [Nasıl yapılır: bir görevi ve alt öğelerini iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
