---
title: Görev iptali
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84da3e1e896397b4e5dacec9d7dd0eeeed96d1c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908927"
---
# <a name="task-cancellation"></a>Görev iptali
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> sınıfları, .NET Framework iptal belirteçlerini kullanımıyla iptal etmeyi destekler. Daha fazla bilgi için [yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md). Görev sınıflarında iptal etme, iptal edilebilir bir işlemi temsil eden kullanıcı temsilcisiyle iptal etmeyi isteyen kod arasında yapılan bir işbirliğini içerir.  Başarılı bir iptal etme isteyen kod arama içerir <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemi ve işlem zamanında sonlandıran bir kullanıcı temsilcisini. Aşağıdaki seçeneklerden birini kullanarak işlemi sonlandırabilirsiniz:  
  
- Yalnızca temsilciden döndürerek. Birçok senaryoda bu yeterlidir; Bu şekilde iptal edilen bir görev örneği geçer ancak <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> durumuna değil <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> durumu.  
  
- Özel durum atma tarafından bir <xref:System.OperationCanceledException> ve iptal istendi belirtece geçirerek. Bunu yapmak için tercih edilen yol kullanmaktır <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> yöntemi. Bu şekilde iptal edilen bir görev, çağıran kodun iptal isteğine yanıt olarak verilen görevi doğrulamak için kullanabileceği İptal Edildi durumuna geçer.  
  
 Aşağıdaki örnekte, özel durum oluşturan görev iptal işlemi için temel düzen gösterilmektedir. Belirtecin kullanıcı temsilcisine ve görev örneğine geçirildiğini unutmayın.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Daha eksiksiz bir örnek için bkz: [nasıl yapılır: Bir görevi ve alt öğelerini iptal](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Olduğunda bir görev örneği uyan bir <xref:System.OperationCanceledException> kullanıcı kodu tarafından oluşturulan, özel durumun belirtecini ilişkili kendi belirteci (görevi oluşturan API'ye geçirilen bir) karşılaştırır. Aynı ve belirtecin olmaları durumunda <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği true döndürürse, görev bunu İptal işlemi Onaylandı olarak yorumlar ve iptal edildi durumuna geçer. Kullanmıyorsanız, bir <xref:System.Threading.Tasks.Task.Wait%2A> veya <xref:System.Threading.Tasks.Task.WaitAll%2A> görev yalnızca durumunu ayarlar görevi beklemek için yöntemi <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Bir görevde iptal edildi durumuna bekliyorsanız bir <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> özel durum (içinde sarmalanmış bir <xref:System.AggregateException> özel durum) oluşturulur. Bu özel durumun, hatalı bir durum yerine başarılı bir iptal işlemini gösterdiğine dikkat edin. Bu nedenle, görevin <xref:System.Threading.Tasks.Task.Exception%2A> özelliği döndürür `null`.  
  
 Belirtecin <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği false döndürürse veya özel durumun belirtecini eşleşmiyorsa belirteci görevin <xref:System.OperationCanceledException> görev hatalı durumuna geçişe neden olan normal bir özel durum gibi değerlendirilir. Ayrıca, başka özel durumların da Görevin Hatalı durumuna geçmesine neden olacağını unutmayın. Tamamlanmış bir görevin durumunu alabilirsiniz <xref:System.Threading.Tasks.Task.Status%2A> özelliği.  
  
 İptal işlemi istendikten sonra görev bazı öğeleri işlemeye devam edebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
- [Nasıl yapılır: Bir görevi ve alt öğelerini iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
