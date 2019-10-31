---
title: SpinWait
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
ms.openlocfilehash: 91588fc6e9c3c8e85de6a315c0743efb0137ecd5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128994"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>, çekirdek olaylar için gereken pahalı bağlam anahtarları ve çekirdek geçişleri önlemek üzere alt düzey senaryolarda kullanabileceğiniz basit bir eşitleme türüdür. Birden çok yerinde bilgisayarda, bir kaynağın uzun süreler boyunca tutulması beklenmiyorsa, bir bekleyen iş parçacığının birkaç düzine veya birkaç yüz döngüsü için Kullanıcı modunda dönmesi daha verimli olabilir ve sonra kaynağı edinmeyi yeniden dener. Kaynak çağrıldıktan sonra kullanılabiliyorsa, birkaç bin döngü kaydettiniz. Kaynak hala kullanılamıyorsa yalnızca birkaç döngü kullanmış ve yine de çekirdek tabanlı bekleme moduna girebiliyor olabilirsiniz. Bu dönen ve daha sonra bekleyen birleşim bazen *iki aşamalı bir bekleme işlemi*olarak adlandırılır.  
  
 <xref:System.Threading.SpinWait>, <xref:System.Threading.ManualResetEvent>gibi çekirdek olaylarını kaydırmak için .NET Framework türleriyle birlikte kullanılmak üzere tasarlanmıştır. <xref:System.Threading.SpinWait>, tek bir programdaki temel dönen işlevsellik için kendisi tarafından da kullanılabilir.  
  
 <xref:System.Threading.SpinWait> yalnızca boş bir döngüden daha fazla. Genel durum için doğru bir dönme davranışı sağlamak üzere dikkatli bir şekilde uygulanır ve yeterince uzun sürirse (yaklaşık olarak bir çekirdek geçişi için gereken süre), içerik anahtarları başlatılır. Örneğin, tek çekirdekli bilgisayarlarda <xref:System.Threading.SpinWait>, dönen tüm iş parçacıklarında ilerlemeleri ilerleme yaptığından, iş parçacığının zaman dilimini hemen verir. <xref:System.Threading.SpinWait> Ayrıca çok çekirdekli makinelerde bile, bekleyen iş parçacığının daha yüksek öncelikli iş parçacıklarını veya çöp toplayıcıyı engellemesini önler. Bu nedenle, iki aşamalı bekleme işleminde bir <xref:System.Threading.SpinWait> kullanıyorsanız, <xref:System.Threading.SpinWait> kendisi bir bağlam anahtarı başlatmadan önce çekirdek beklemeyi çağırmanız önerilir. <xref:System.Threading.SpinWait>, <xref:System.Threading.SpinWait.SpinOnce%2A>her çağrıdan önce kontrol ettiğiniz <xref:System.Threading.SpinWait.NextSpinWillYield%2A> özelliğini sağlar. Özellik `true`döndürdüğünde, kendi bekleme işleminizi başlatın. Bir örnek için bkz. [nasıl yapılır: Iki aşamalı bir bekleme Işlemini uygulamak Için SpinWait kullanma](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 İki aşamalı bir bekleme işlemi gerçekleştirmemekle kalmaz ancak bazı koşullar doğru olana kadar yalnızca bir koşul true oluncaya kadar <xref:System.Threading.SpinWait>, Windows işletim sistemi ortamında iyi bir vatandaşlık olacak şekilde, onun bağlam anahtarlarını gerçekleştirmesini sağlayabilirsiniz. Aşağıdaki temel örnek, kilit içermeyen bir yığında <xref:System.Threading.SpinWait> gösterir. Yüksek performanslı, iş parçacığı açısından güvenli bir yığına ihtiyacınız varsa <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>kullanmayı düşünün.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.SpinWait%2A>
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
