---
title: 'Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: 5bac174660177fd47e1f345e64581e35ae4c0ffc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137950"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma
Aşağıdaki örnek, iki aşamalı <xref:System.Threading.SpinWait?displayProperty=nameWithType> bir bekleme işlemi uygulamak için bir nesnenin nasıl kullanılacağını gösterir. İlk aşamada, eşitleme nesnesi, `Latch`bir , kilit kullanılabilir hale gelip gelmediğini denetler ken birkaç döngü için döner. İkinci aşamada, kilit kullanılabilir hale gelirse, `Wait` o zaman <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> yöntemi bekleme gerçekleştirmek için kullanmadan döndürür; aksi `Wait` takdirde, bekleme gerçekleştirir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir Mandal eşitleme ilkel çok temel bir uygulama gösterir. Bekleme sürelerinin çok kısa olması beklenirken bu veri yapısını kullanabilirsiniz. Bu örnek yalnızca gösteri amaçlıdır. Programınızda mandal türü işlevselliği gerekiyorsa, 'yi kullanmayı <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>düşünün.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Mandal, <xref:System.Threading.SpinWait> iş parçacığının zaman dilimini `SpinOnce` verim <xref:System.Threading.SpinWait> almasına neden olmak için nesneyi yalnızca bir sonraki çağrıya kadar yerinde döndürmek için kullanır. Bu noktada, mandal, zaman atlama <xref:System.Threading.WaitHandle.WaitOne%2A> değerinin <xref:System.Threading.ManualResetEvent> geri kalanını çağırArak ve geçirerek kendi bağlam anahtarına neden olur.  
  
 Günlüğe kaydetme çıktısı, Mandal'ın kilidi kullanmadan kilidi <xref:System.Threading.ManualResetEvent>edinerek performansı ne sıklıkta artırabildiğini gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SpinWait](../../../docs/standard/threading/spinwait.md)
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
