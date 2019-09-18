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
ms.openlocfilehash: afc0fd47e51723a7b3ba1b07dffc49260f88917d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052779"
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged MDA
Yönetilen `gcManagedToUnmanaged` hata ayıklama Yardımcısı (MDA), bir iş parçacığı yönetilen 'ten yönetilmeyen koda geçiş yaptığında çöp toplamaya neden olur.  
  
## <a name="symptoms"></a>Belirtiler  
 Yönetilmeyen bir Kullanıcı bileşeni, COM 'a sunulan bir yönetilen nesneyi kullanmaya çalışırken bir erişim ihlali oluşturur. COM nesnesi yayımlanmış gibi görünüyor. Erişim ihlali belirleyici olmayan bir değer.  
  
## <a name="cause"></a>Sebep  
 Yönetilmeyen bir bileşen, yönetilen bir COM nesnesini doğru bir şekilde saymadığı takdirde, yönetilmeyen bileşen nesneye bir başvuru tuttuğunda, çalışma zamanı COM 'a sunulan bir yönetilen nesne toplayabilir. Çöp koleksiyonları sırasında <xref:System.Runtime.InteropServices.Marshal.Release%2A> çalışma zamanı çağırır, bu nedenle Kullanıcı bileşeni atık toplama gerçekleşmeden önce nesneyi kullanıyorsa, henüz toplanmamıştır. Bu, belirleyici olmayan bir ISM kaynağıdır.  
  
## <a name="resolution"></a>Çözüm  
 Bu yardımcıyı etkinleştirmek, nesnenin koleksiyon için uygun olduğu zaman arasındaki süreyi azaltır ve <xref:System.Runtime.InteropServices.Marshal.Release%2A> çağrılır, hangi yönetilmeyen bileşenin ilk olarak toplanan nesneye erişmeye çalıştığını izlemeye yardımcı olur.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Her iş parçacığı yönetilen 'ten yönetilmeyen koda geçiş yaptığında çöp toplamaya neden olur.  
  
## <a name="output"></a>Çıkış  
 Bu MDA hiçbir çıkış üretmez.  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
