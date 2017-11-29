---
title: gcManagedToUnmanaged MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1aa528eb2acc872b1956edef3af3724bb3b54d67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged MDA
`gcManagedToUnmanaged` Yönetilen hata ayıklama Yardımcısı (MDA) yönetilmeyen kod için yönetilen bir iş parçacığı gelen geçiş her bir atık toplama neden olur.  
  
## <a name="symptoms"></a>Belirtiler  
 Bir yönetilmeyen kullanıcı bileşeni COM'a gösterilen yönetilen bir nesnenin kullanmaya çalışırken bir erişim ihlali oluşturur COM nesnesi çıkarılan görünüyor. Erişim ihlali belirleyici değildir.  
  
## <a name="cause"></a>Sebep  
 Yönetilmeyen bir bileşen başvuru yönetilen bir COM nesnesi düzgün sayım değilse, çalışma zamanı yönetilmeyen bileşen hala nesneye bir başvurusu tuttuğunda com'a yönetilen bir nesnenin toplamak. Çalışma zamanı çağrıları <xref:System.Runtime.InteropServices.Marshal.Release%2A> çöp koleksiyonları sırasında şekilde çöp toplama oluşmadan önce kullanıcı Bileşen Nesne kullanıyorsa, sonra henüz alınamadı. Bu nondeterminism kaynağıdır.  
  
## <a name="resolution"></a>Çözüm  
 Bu Yardımcısı'nı etkinleştirme nesnesi için koleksiyonu uygun olduğunda arasında geçen zamanı azaltır ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> olarak adlandırılan, yönetilmeyen hangi bileşenin ilk toplanan nesne erişmeye çalıştığında aşağı izlemek için yardımcı olur.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Yönetilmeyen kod için bir iş parçacığı geçişler yönetilen her bir atık toplama neden olur.  
  
## <a name="output"></a>Çıkış  
 Bu MDA herhangi bir çıktı oluşturmaz.  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)  
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
