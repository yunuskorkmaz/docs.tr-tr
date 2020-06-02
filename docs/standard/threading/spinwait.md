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
ms.openlocfilehash: 8b98e7d8b8ea4578fb446a0587f9a46ba4271348
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291116"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>, çekirdek olaylar için gereken pahalı bağlam anahtarları ve çekirdek geçişleri önlemek üzere alt düzey senaryolarda kullanabileceğiniz basit bir eşitleme türüdür. Birden çok yerinde bilgisayarda, bir kaynağın uzun süreler boyunca tutulması beklenmiyorsa, bir bekleyen iş parçacığının birkaç düzine veya birkaç yüz döngüsü için Kullanıcı modunda dönmesi daha verimli olabilir ve sonra kaynağı edinmeyi yeniden dener. Kaynak çağrıldıktan sonra kullanılabiliyorsa, birkaç bin döngü kaydettiniz. Kaynak hala kullanılamıyorsa yalnızca birkaç döngü kullanmış ve yine de çekirdek tabanlı bekleme moduna girebiliyor olabilirsiniz. Bu dönen ve daha sonra bekleyen birleşim bazen *iki aşamalı bir bekleme işlemi*olarak adlandırılır.  
  
 <xref:System.Threading.SpinWait>, gibi çekirdek olaylarını kaydırmak için .NET Framework türleriyle birlikte kullanılmak üzere tasarlanmıştır <xref:System.Threading.ManualResetEvent> . <xref:System.Threading.SpinWait>, tek bir programdaki temel dönen işlevsellik için kendisi tarafından da kullanılabilir.  
  
 <xref:System.Threading.SpinWait>yalnızca boş bir döngüden daha fazla. Genel durum için doğru bir dönme davranışı sağlamak üzere dikkatli bir şekilde uygulanır ve yeterince uzun sürirse (yaklaşık olarak bir çekirdek geçişi için gereken süre), içerik anahtarları başlatılır. Örneğin, tek çekirdekli bilgisayarlarda, <xref:System.Threading.SpinWait> dönen blok tüm iş parçacıklarında ilerleme yaptığından, iş parçacığının zaman dilimini hemen oluşturur. <xref:System.Threading.SpinWait>Ayrıca, bekleyen iş parçacığının daha yüksek öncelikli iş parçacıklarını veya çöp toplayıcıyı engellemesini engellemek için çok çekirdekli makinelerde bile. Bu nedenle, <xref:System.Threading.SpinWait> iki aşamalı bekleme işleminde bir kullanıyorsanız, <xref:System.Threading.SpinWait> kendisi bir bağlam anahtarı başlatmadan önce çekirdek beklemeyi çağırmanız önerilir. <xref:System.Threading.SpinWait><xref:System.Threading.SpinWait.NextSpinWillYield%2A>, ' a her çağrıdan önce kontrol edebilirsiniz özelliğini sağlar <xref:System.Threading.SpinWait.SpinOnce%2A> . Özelliği döndüğünde `true` , kendi bekleme işleminizi başlatın. Bir örnek için bkz. [nasıl yapılır: Iki aşamalı bir bekleme Işlemini uygulamak Için SpinWait kullanma](how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 İki aşamalı bir bekleme işlemi gerçekleştirmemekle kalmaz ancak bazı koşullar doğru olana kadar yalnızca, <xref:System.Threading.SpinWait> Windows işletim sistemi ortamında iyi bir vatandaşlık olması için bağlam anahtarlarını gerçekleştirmeye olanak sağlayabilirsiniz. Aşağıdaki temel örnek, bir <xref:System.Threading.SpinWait> kilit boş yığında bir gösterir. Yüksek performanslı, iş parçacığı açısından güvenli bir yığına ihtiyacınız varsa, kullanmayı göz önünde bulundurun <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> .  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.SpinWait%2A>
- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
