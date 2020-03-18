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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139976"
---
# <a name="task-cancellation"></a>Görev iptali
Ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> sınıflar .NET Framework'de iptal belirteçleri kullanarak iptali destekler. Daha fazla bilgi için Yönetilen [İş Parçacıklarında İptal'e](../../../docs/standard/threading/cancellation-in-managed-threads.md)bakın. Görev sınıflarında iptal etme, iptal edilebilir bir işlemi temsil eden kullanıcı temsilcisiyle iptal etmeyi isteyen kod arasında yapılan bir işbirliğini içerir.  Başarılı bir iptal, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> yöntemi çağıran isteyen kodu ve kullanıcı temsilcisinin işlemi zamanında sonlandırmasını içerir. Aşağıdaki seçeneklerden birini kullanarak işlemi sonlandırabilirsiniz:  
  
- Yalnızca temsilciden döndürerek. Birçok senaryoda bu yeterlidir; ancak, bu şekilde iptal edilen bir görev örneği <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> duruma değil, duruma geçiş eder.  
  
- Bir <xref:System.OperationCanceledException> atarak ve iptal talep edildi belirteci geçirerek. Bunu yapmanın tercih edilen yolu <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> yöntemi kullanmaktır. Bu şekilde iptal edilen bir görev, çağıran kodun iptal isteğine yanıt olarak verilen görevi doğrulamak için kullanabileceği İptal Edildi durumuna geçer.  
  
 Aşağıdaki örnekte, özel durum oluşturan görev iptal işlemi için temel düzen gösterilmektedir. Belirtecin kullanıcı temsilcisine ve görev örneğine geçirildiğini unutmayın.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Daha eksiksiz bir örnek için [bkz: Görevi Ve Çocukları İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Bir görev örneği kullanıcı <xref:System.OperationCanceledException> kodu tarafından atılan bir durumu gözlemlediğinde, özel durum belirteciyle ilişkili belirteciyle (Görevi oluşturan API'ye geçirilen belirteç) karşılaştırır. Bunlar aynıysa ve belirteç <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği doğru döndürürse, görev bunu iptali kabul etmek ve İptal edilen duruma geçişler olarak yorumlar. Görevi beklemek için <xref:System.Threading.Tasks.Task.Wait%2A> bir <xref:System.Threading.Tasks.Task.WaitAll%2A> veya yöntem kullanmazsanız, görev durumunu <xref:System.Threading.Tasks.TaskStatus.Canceled>sadece .  
  
 İptal edilen duruma geçiş yapan bir Görevi bekliyorsanız, <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> bir <xref:System.AggregateException> özel durum (özel duruma sarılmış) atılır. Bu özel durumun, hatalı bir durum yerine başarılı bir iptal işlemini gösterdiğine dikkat edin. Bu nedenle, görevin <xref:System.Threading.Tasks.Task.Exception%2A> `null`özelliği döndürür.  
  
 Belirteci <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği yanlış dönerse veya özel durum belirteci Görev'in belirteciyle <xref:System.OperationCanceledException> eşleşmiyorsa, görevin Hatalı duruma geçmesine neden olan normal bir özel durum olarak kabul edilir. Ayrıca, başka özel durumların da Görevin Hatalı durumuna geçmesine neden olacağını unutmayın. Tamamlanan görevin durumunu <xref:System.Threading.Tasks.Task.Status%2A> özellikte alabilirsiniz.  
  
 İptal işlemi istendikten sonra görev bazı öğeleri işlemeye devam edebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
- [Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
