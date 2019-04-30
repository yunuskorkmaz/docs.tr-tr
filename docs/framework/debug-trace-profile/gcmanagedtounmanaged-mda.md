---
title: gcManagedToUnmanaged MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7bb4779e300df71a5d075a322bcac8398ce42f34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754446"
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged MDA
`gcManagedToUnmanaged` Yönetilen hata ayıklama Yardımcısı (MDA) yönetilmeyen kod için yönetilen bir iş parçacığı gelen geçiş her bir çöp toplamanın neden olur.  
  
## <a name="symptoms"></a>Belirtiler  
 Yönetilmeyen kullanıcı bileşeni COM tarafından sunulan bir yönetilen nesne kullanmaya çalışırken bir erişim ihlali oluşturur COM nesnesi yayımlanan görünüyor. Erişim ihlali belirleyici değildir.  
  
## <a name="cause"></a>Sebep  
 Yönetilmeyen bir bileşene başvuru yönetilen bir COM nesnesi düzgün sayımı değilse, çalışma zamanının yönetilen bir nesnenin yönetilmeyen bileşeni hala nesnesine bir başvuru tuttuğunda com'a toplamanız mümkündü. Çalışma zamanı çağrıları <xref:System.Runtime.InteropServices.Marshal.Release%2A> atık toplama sırasında kadar çöp toplama oluşmadan önce nesne kullanıcı bileşen kullanıyorsa, ardından bunu değil henüz toplanmış olabilir. Bu nondeterminism kaynağıdır.  
  
## <a name="resolution"></a>Çözüm  
 Bu Yardımcısı'nı etkinleştirme, nesne koleksiyonu için uygun olduğunda arasındaki süreyi azaltır ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> olarak adlandırılan, hangi yönetilmeyen bileşen önce toplanan nesneye erişme girişiminde aşağı izlemek için yardımcı olur.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bir iş parçacığı geçişler yönetilmeyen kod için yönetilen her bir çöp toplamanın neden olur.  
  
## <a name="output"></a>Çıkış  
 Bu mda'nın herhangi bir çıktı üretmez.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
- [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
