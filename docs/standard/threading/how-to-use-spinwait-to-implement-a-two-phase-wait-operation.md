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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137950"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma
Aşağıdaki örnek, iki aşamalı bir bekleme işlemini uygulamak için bir <xref:System.Threading.SpinWait?displayProperty=nameWithType> nesnesinin nasıl kullanılacağını gösterir. İlk aşamada, eşitleme nesnesi `Latch`, kilidin kullanılabilir olup olmadığını denetlerken birkaç döngü için döner. İkinci aşamada, kilit kullanılabilir hale gelirse `Wait` yöntemi, bekleme işlemini gerçekleştirmek için <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> kullanılmadan döndürülür; Aksi takdirde, `Wait` bekleme işlemini gerçekleştirir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir mandal eşitleme temel öğesinin çok basit bir uygulamasını gösterir. Bu veri yapısını, bekleme sürelerinin çok kısa olması beklendiğinde kullanabilirsiniz. Bu örnek yalnızca tanıtım amaçlıdır. Programınızda mandal türü işlevselliğe ihtiyacınız varsa <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>kullanmayı göz önünde bulundurun.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Mandal, `SpinOnce` bir sonraki çağrıya <xref:System.Threading.SpinWait>, iş parçacığının zaman dilimini almasına neden olana kadar yerine geçmek için <xref:System.Threading.SpinWait> nesnesini kullanır. Bu noktada, mandal, <xref:System.Threading.ManualResetEvent> <xref:System.Threading.WaitHandle.WaitOne%2A> çağırarak ve zaman aşımı değerinin geri kalanını geçirerek kendi bağlam anahtarına neden olur.  
  
 Günlüğe kaydetme çıktısı, <xref:System.Threading.ManualResetEvent>kullanmadan kilidi alarak mandalın performansı ne sıklıkla artırabilmesini gösterir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SpinWait](../../../docs/standard/threading/spinwait.md)
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
