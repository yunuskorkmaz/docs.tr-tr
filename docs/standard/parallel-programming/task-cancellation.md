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
ms.openlocfilehash: 17cabde95644dbc1584dd85b99e26ff7c5cb686d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139976"
---
# <a name="task-cancellation"></a>Görev iptali
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> sınıfları, .NET Framework iptal belirteçleri kullanılarak iptali destekler. Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md). Görev sınıflarında iptal etme, iptal edilebilir bir işlemi temsil eden kullanıcı temsilcisiyle iptal etmeyi isteyen kod arasında yapılan bir işbirliğini içerir.  Başarılı bir iptal etme, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemini çağıran istekte bulunan kodu ve kullanıcı temsilcisinin işlemi zamanında sonlandırmasını içerir. Aşağıdaki seçeneklerden birini kullanarak işlemi sonlandırabilirsiniz:  
  
- Yalnızca temsilciden döndürerek. Birçok senaryoda bu yeterlidir; Ancak, bu şekilde iptal edilen bir görev örneği, <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> durumuna değil <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> duruma geçer.  
  
- <xref:System.OperationCanceledException> oluşturup iptalinin istendiği belirteci geçirerek. Bunu yapmanın tercih edilen yolu <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> yöntemi kullanmaktır. Bu şekilde iptal edilen bir görev, çağıran kodun iptal isteğine yanıt olarak verilen görevi doğrulamak için kullanabileceği İptal Edildi durumuna geçer.  
  
 Aşağıdaki örnekte, özel durum oluşturan görev iptal işlemi için temel düzen gösterilmektedir. Belirtecin kullanıcı temsilcisine ve görev örneğine geçirildiğini unutmayın.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Daha kapsamlı bir örnek için bkz. [nasıl yapılır: bir görevi ve alt öğelerini Iptal etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Bir görev örneği, Kullanıcı kodu tarafından oluşturulan bir <xref:System.OperationCanceledException> hizmet veriyorsa, özel durumun belirtecini ilişkili belirteçle karşılaştırır (görevi oluşturan API 'ye geçirilen bir tane). Bunlar aynıysa ve belirtecin <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği true değerini döndürürse, görev bunu iptal etme ve Iptal edilen duruma geçiş olarak yorumlar. Görevi beklemek için bir <xref:System.Threading.Tasks.Task.Wait%2A> veya <xref:System.Threading.Tasks.Task.WaitAll%2A> yöntemi kullanmıyorsanız, görev durumunu yalnızca <xref:System.Threading.Tasks.TaskStatus.Canceled>olarak ayarlar.  
  
 Iptal edilen duruma geçiş yapan bir görevi bekliyorsa, bir <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> özel durumu (<xref:System.AggregateException> özel durumunda sarmalanmış) oluşturulur. Bu özel durumun, hatalı bir durum yerine başarılı bir iptal işlemini gösterdiğine dikkat edin. Bu nedenle, görevin <xref:System.Threading.Tasks.Task.Exception%2A> özelliği `null`döndürür.  
  
 Belirtecin <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği false döndürürse veya özel durumun belirteci görevin belirteciyle eşleşmezse, <xref:System.OperationCanceledException> normal özel durum gibi değerlendirilir ve görevin hatalı duruma geçmesine neden olur. Ayrıca, başka özel durumların da Görevin Hatalı durumuna geçmesine neden olacağını unutmayın. <xref:System.Threading.Tasks.Task.Status%2A> özelliğindeki tamamlanan görevin durumunu alabilirsiniz.  
  
 İptal işlemi istendikten sonra görev bazı öğeleri işlemeye devam edebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
- [Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
