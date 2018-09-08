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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dcb2fbf5e0a310156fdc6fac5fe736692e8ec133
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135347"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Nasıl yapılır: İki Aşamalı bir Bekleme İşlemini Uygulamak için SpinWait Kullanma
Aşağıdaki örnek nasıl kullanılacağını gösteren bir <xref:System.Threading.SpinWait?displayProperty=nameWithType> aşamalı bir bekleme işlemini uygulamak için nesne. İlk aşamada, eşitleme nesnesi bir `Latch`, kilit kullanılabilir hale olup olmadığını denetlerken birkaç döngü için döner. İkinci kısımda kilit kullanılabilir durumdaysa, ardından `Wait` yöntemi döndürür kullanmadan <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> beklemesi; gerçekleştirmek için Aksi takdirde, `Wait` bekleme gerçekleştirir.  
  
## <a name="example"></a>Örnek  
 Bu örnek çok basit bir uygulama bir Mandal eşitleme ilkel gösterir. Bekleme süresini çok kısa olması beklendiğinde bu veri yapısını kullanabilirsiniz. Bu örnek yalnızca gösterim amaçlıdır. Tutma türü işlevselliği programınıza gerektirir kullanmayı <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Mandal kullanır <xref:System.Threading.SpinWait> yapılan sonraki çağrıda kadar yalnızca yerinde dönmeye nesne `SpinOnce` neden <xref:System.Threading.SpinWait> iş parçacığının zaman dilimi bekletilemiyor. Bu noktada, Mandal çağırarak kendi içerik anahtarı neden <xref:System.Threading.WaitHandle.WaitOne%2A> üzerinde <xref:System.Threading.ManualResetEvent> ve zaman aşımı değerini geri kalanında geçirme.  
  
 Mandal ne sıklıkta kullanmadan kilit alınırken tarafından performansını artırabilirsiniz günlük çıktısını gösterir <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [SpinWait](../../../docs/standard/threading/spinwait.md)  
- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)
