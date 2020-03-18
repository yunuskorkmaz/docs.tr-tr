---
title: 'Nasıl Yapılır: Yoklama ile İptal İsteklerini Dinleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
ms.openlocfilehash: df76674e3003bbb77ef062e90b1dc3283f681d35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138019"
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a>Nasıl Yapılır: Yoklama ile İptal İsteklerini Dinleme
Aşağıdaki örnek, kullanıcı kodunun arama iş parçacığından iptal talebinde bulunulup bulunulmadığını görmek için iptal jetonunu düzenli aralıklarla yoklamanın bir yolunu gösterir. Bu örnek <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> türü kullanır, ancak aynı desen <xref:System.Threading.ThreadPool?displayProperty=nameWithType> doğrudan tür veya <xref:System.Threading.Thread?displayProperty=nameWithType> tür tarafından oluşturulan eşzamanlı işlemler için geçerlidir.  
  
## <a name="example"></a>Örnek  
 Yoklama, Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliğinin değerini düzenli olarak okuyabilen bir tür döngü veya özyinelemeli kod gerektirir. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Türü kullanıyorsanız ve görevin arama iş parçacığı üzerinde tamamlanmasını bekliyorsanız, <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> özelliği denetlemek ve özel durumu atmak için yöntemi kullanabilirsiniz. Bu yöntemi kullanarak, bir isteğe yanıt olarak doğru özel durum atıldığından emin olun. Eğer kullanıyorsanız <xref:System.Threading.Tasks.Task>, o zaman bu yöntemi arama <xref:System.OperationCanceledException>el ile atma daha iyidir . Eğer özel durum atmak zorunda değilseniz, o zaman sadece özelliği kontrol edebilir `true`ve özellik ise yöntemden dönebilirsiniz.  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 Arama <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> son derece hızlı dır ve döngüler içinde önemli ek yükü tanıtmak değildir.  
  
 Arıyorsanız, <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>iptale yanıt olarak özel <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> durum atmanın yanı sıra yapmanız gereken başka bir iş varsa, yalnızca özelliği açıkça kontrol etmeniz gerekir. Bu örnekte, kodun gerçekten özelliğe iki kez eriştiğini görebilirsiniz: <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> açık erişimde bir kez ve yöntemde tekrar. Ancak <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> özelliği okuma eylemi erişim başına yalnızca bir değişken okuma yönergesi içerdiğinden, çift erişim performans açısından önemli değildir. Yine de yöntemi el ile atmak yerine aramak <xref:System.OperationCanceledException>tercih edilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen İş Parçacıklarında İptal](../../../docs/standard/threading/cancellation-in-managed-threads.md)
