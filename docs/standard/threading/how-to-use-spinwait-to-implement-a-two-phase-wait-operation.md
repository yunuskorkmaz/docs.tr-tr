---
title: 'Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: e5d58067f70706294308952b9f7cfbf69fa89a58
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728491"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma

Aşağıdaki örnek, bir <xref:System.Threading.SpinWait?displayProperty=nameWithType> nesnenin iki aşamalı bir bekleme işlemini uygulamak için nasıl kullanılacağını gösterir. İlk aşamada, eşitleme nesnesi a, `Latch` kilidin kullanılabilir olup olmadığını kontrol ederken birkaç döngü için döner. İkinci aşamada, kilit kullanılabilir hale gelirse, `Wait` yöntemi <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> beklemeyi gerçekleştirmek için kullanılmadan döner; Aksi takdirde, `Wait` beklemeyi gerçekleştirir.  
  
## <a name="example"></a>Örnek  

 Bu örnek, bir mandal eşitleme temel öğesinin çok basit bir uygulamasını gösterir. Bu veri yapısını, bekleme sürelerinin çok kısa olması beklendiğinde kullanabilirsiniz. Bu örnek yalnızca tanıtım amaçlıdır. Programınızda mandal türü işlevselliğe ihtiyacınız varsa kullanmayı göz önünde bulundurun <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> .  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Mandal, <xref:System.Threading.SpinWait> yalnızca bir sonraki çağrıya, `SpinOnce` <xref:System.Threading.SpinWait> iş parçacığının zaman dilimini vermesine neden olana kadar yerine dönmesi için nesnesini kullanır. Bu noktada, mandal, <xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.ManualResetEvent> zaman aşımı değerinin geri kalanını geçirerek ve ' ı çağırarak kendi bağlam anahtarına neden olur.  
  
 Günlüğe kaydetme çıktısı, ' i kullanmadan kilidi alarak mandalın performansı ne sıklıkta artırabiltiğini gösterir <xref:System.Threading.ManualResetEvent> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SpinWait](spinwait.md)
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
