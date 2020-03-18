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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128994"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>çekirdek olayları için gerekli olan pahalı bağlam anahtarlarını ve çekirdek geçişlerini önlemek için düşük düzeyli senaryolarda kullanabileceğiniz hafif bir eşitleme türüdür. Çok çekirdekli bilgisayarlarda, bir kaynağın uzun süre tutulması beklenmiyorsa, bekleyen bir iş parçacığının birkaç düzine veya birkaç yüz döngü boyunca kullanıcı modunda dönmesi ve sonra kaynağı yeniden elde etmesi daha verimli olabilir. Kaynak döndükten sonra kullanılabilirse, birkaç bin döngü kaydetmiş sinizdemektir. Kaynak hala kullanılamıyorsa, yalnızca birkaç döngü harcadınız demektir ve çekirdek tabanlı beklemeye devam edebilirsiniz. Bu döndürme-sonra-bekleme birleşimi bazen *iki aşamalı bekleme işlemi*olarak adlandırılır.  
  
 <xref:System.Threading.SpinWait>gibi çekirdek olayları sarma .NET Framework türleri ile birlikte kullanılmak <xref:System.Threading.ManualResetEvent>üzere tasarlanmıştır. <xref:System.Threading.SpinWait>tek bir programda temel eğirme işlevselliği için de tek başına kullanılabilir.  
  
 <xref:System.Threading.SpinWait>boş bir döngüden daha fazlasıdır. Genel servis talebi için doğru eğirme davranışı sağlamak için dikkatle uygulanır ve yeterince uzun dönerse bağlam anahtarlarının kendisi (çekirdek geçişi için gereken süre kabaca) başlatılır. Örneğin, tek çekirdekli bilgisayarlarda, <xref:System.Threading.SpinWait> dönen bloklar tüm iş parçacıklarında ilerleme kaydettiğinden, iş parçacığının zaman dilimini hemen verir. <xref:System.Threading.SpinWait>ayrıca, bekleyen iş parçacığının daha yüksek öncelikli iş parçacığı veya çöp toplayıcısını engellemesini önlemek için çok çekirdekli makinelerde bile verim verir. Bu nedenle, iki <xref:System.Threading.SpinWait> aşamalı bir bekleme işleminde bir tane kullanıyorsanız, <xref:System.Threading.SpinWait> çekirdek beklemeyi kendisi bir bağlam anahtarı başlatmadan önce çağırmanızı öneririz. <xref:System.Threading.SpinWait>her <xref:System.Threading.SpinWait.NextSpinWillYield%2A> aramadan önce kontrol edebilirsiniz <xref:System.Threading.SpinWait.SpinOnce%2A>özelliği sağlar. Özellik döndüğünde, `true`kendi Bekle işleminizi başlatın. Örneğin, [bkz.](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md)  
  
 İki aşamalı bir bekleme işlemi gerçekleştirmiyorsanız ancak bazı koşullar doğru olana <xref:System.Threading.SpinWait> kadar dönüyorsanız, Windows işletim sistemi ortamında iyi bir vatandaş olacak şekilde bağlam anahtarlarını gerçekleştirmeyi etkinleştirebilirsiniz. Aşağıdaki temel örnek, <xref:System.Threading.SpinWait> kilitsiz bir yığındaki bir a'yı gösterir. Yüksek performanslı, iş parçacığı güvenli bir yığın <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>gerekiyorsa, kullanmayı düşünün.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Thread.SpinWait%2A>
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
