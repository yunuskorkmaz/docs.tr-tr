---
title: Görev iptali
description: .NET 'teki iptal belirteçleri kullanılarak görev ve görev sınıflarında desteklenen görev iptalini anlayın <TResult> .
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
ms.openlocfilehash: deea3eaaa1e652d44a71e953975d776d4898a9b3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830018"
---
# <a name="task-cancellation"></a>Görev iptali

<xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Ve sınıfları, iptal <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> belirteçleri kullanılarak iptali destekler. Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında iptal](../threading/cancellation-in-managed-threads.md). Görev sınıflarında, iptal, iptal edilebilen bir işlemi ve iptali istenen kodu temsil eden kullanıcı temsilcisi arasındaki ortak işlemi içerir. Başarılı bir iptal etme yöntemi çağıran istekte bulunan kodu <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> ve kullanıcı temsilcisinin işlemi zamanında sonlandırmasını içerir. Aşağıdaki seçeneklerden birini kullanarak işlemi sonlandırabilirsiniz:  
  
- Yalnızca temsilciden döndürerek. Birçok senaryoda bu yeterlidir; Ancak, bu şekilde iptal edilen bir görev örneği duruma göre <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> değil, duruma geçer <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> .  
  
- Bir <xref:System.OperationCanceledException> oluşturup, iptal etme isteğinde bulunan belirteci geçirerek. Bunu yapmanın tercih edilen yolu <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> yöntemi kullanmaktır. Bu şekilde iptal edilen bir görev, çağıran kodun iptal isteğine yanıt olarak verilen görevi doğrulamak için kullanabileceği İptal Edildi durumuna geçer.  
  
 Aşağıdaki örnekte, özel durum oluşturan görev iptal işlemi için temel düzen gösterilmektedir. Belirtecin kullanıcı temsilcisine ve görev örneğine geçirildiğini unutmayın.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Daha kapsamlı bir örnek için bkz. [nasıl yapılır: bir görevi ve alt öğelerini Iptal etme](how-to-cancel-a-task-and-its-children.md).  
  
 Bir görev örneği, <xref:System.OperationCanceledException> Kullanıcı kodu tarafından oluşturulan bir görev olduğunda, özel durumun belirtecini ilişkili belirteçle karşılaştırır (görevi oluşturan API 'ye geçirilen bir tane). Bunlar aynıysa ve belirtecin <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği true değerini döndürürse, görev bunu iptal etme ve Iptal edilen duruma geçiş olarak yorumlar. <xref:System.Threading.Tasks.Task.Wait%2A> <xref:System.Threading.Tasks.Task.WaitAll%2A> Görevi beklemek için bir veya yöntemi kullanmıyorsanız, görev durumunu yalnızca olarak ayarlar <xref:System.Threading.Tasks.TaskStatus.Canceled> .  
  
 Iptal edilen duruma geçiş yapan bir görevi bekliyorsa, bir <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> özel durum (özel bir durumda sarmalanmış <xref:System.AggregateException> ) oluşturulur. Bu özel durumun, hatalı bir durum yerine başarılı bir iptal işlemini gösterdiğine dikkat edin. Bu nedenle, görevin <xref:System.Threading.Tasks.Task.Exception%2A> özelliği döndürür `null` .  
  
 Belirtecin <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği false döndürürse veya özel durumun belirteci görevin belirteciyle eşleşmezse, <xref:System.OperationCanceledException> normal özel durum gibi davranır ve görevin hatalı duruma geçmesine neden olur. Ayrıca, başka özel durumların da Görevin Hatalı durumuna geçmesine neden olacağını unutmayın. Özelliğindeki tamamlanmış görevin durumunu alabilirsiniz <xref:System.Threading.Tasks.Task.Status%2A> .  
  
 İptal işlemi istendikten sonra görev bazı öğeleri işlemeye devam edebilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Iş parçacıklarında iptal](../threading/cancellation-in-managed-threads.md)
- [Nasıl yapılır: Bir Görevi ve Alt Öğelerini İptal Etme](how-to-cancel-a-task-and-its-children.md)
