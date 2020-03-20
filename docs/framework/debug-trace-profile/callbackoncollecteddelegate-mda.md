---
title: callbackOnCollectedDelegate MDA
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- managed debugging assistants (MDAs), callback on collected delegates
- MDAs (managed debugging assistants), callback on collected delegates
- callback on delegate after garbage collection
- callbackOnCollectedDelegate MDA
- managed debugging assistants (MDAs), garbage collection
- call back collected delegates
- garbage collection, run-time errors
- delegates [.NET Framework], garbage collection
ms.assetid: 398b0ce0-5cc9-4518-978d-b8263aa21e5b
ms.openlocfilehash: d4ca777fa5b41433eec227762fe315f22ab33cf6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174231"
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate MDA
Yönetilen `callbackOnCollectedDelegate` hata ayıklama yardımcısı (MDA), bir temsilci yönetilen koddan işlev işaretçisi olarak denetlenirse etkinleştirilir ve temsilci çöp toplandıktan sonra bu işlev işaretçisine bir geri arama yerleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Erişim ihlalleri, yönetilen temsilcilerden alınan işlev işaretçileri aracılığıyla yönetilen koda çağrı yapmaya çalışırken oluşur. Bu hatalar, yaygın dil çalışma zamanı (CLR) hataları olmasa da, erişim ihlali CLR kodunda oluştuğundan öyle görünebilir.  
  
 Hata tutarlı değildir; bazen işlev işaretçisi üzerindeki çağrı başarılı olur ve bazen başarısız olur. Hata yalnızca ağır yük altında veya rasgele sayıda denemede oluşabilir.  
  
## <a name="cause"></a>Nedeni  
 İşlev işaretçisinin oluşturulduğu ve yönetilmeyen koda maruz kalan temsilci çöp toplandı. Yönetilmeyen bileşen işlev işaretçisini çağırmaya çalıştığında, bir erişim ihlali oluşturur.  
  
 Çöp toplamanın ne zaman oluştuğuna bağlı olduğundan hata rasgele görünür. Bir temsilci toplama için uygunsa, geri arama dan sonra çöp toplama oluşabilir ve arama başarılı olur. Diğer zamanlarda, çöp toplama geri arama önce oluşur, geri arama bir erişim ihlali oluşturur ve program durur.  
  
 Hata olasılığı, temsilciyi mareşalleme ile işlev işaretçisindeki geri arama arasındaki süreye ve çöp koleksiyonlarının sıklığına bağlıdır. Temsilci yimareme ile takip eden geri arama arasındaki süre kısaysa, başarısızlık düzensizdir. İşlev işaretçisini alan yönetilmeyen yöntem işlev işaretçisini daha sonra kullanmak üzere kaydetmez, bunun yerine işlev işaretçisini geri çağırıp dönmeden önce işlemini tamamlamak için hemen geri çağırırsa, genellikle durum böyledir. Benzer şekilde, bir sistem ağır yük altında yken daha fazla çöp toplama oluşur, bu da geri çağırmadan önce bir çöp toplamanın oluşma olasılığını arttırır.  
  
## <a name="resolution"></a>Çözüm  
 Bir temsilci yönetilmeyen bir işlev işaretçisi olarak sıralandıktan sonra, çöp toplayıcı ömrünü izleyemez. Bunun yerine, kodunuz yönetilmeyen işlev işaretçisinin ömrü boyunca temsilciye bir başvuru tutmalı. Ancak bunu yapmadan önce hangi temsilcinin toplandığını belirlemeniz gerekir. MDA etkinleştirildiğinde, temsilcinin tür adını sağlar. Bu temsilciyi yönetilmeyen koda aktaran platform çağrısı veya COM imzaları için kodunuzu aramak için bu adı kullanın. Kusurlu temsilci bu çağrı sitelerinden biri üzerinden dağıtılır. Ayrıca, MDA'nın `gcUnmanagedToManaged` her geri aramadan önce bir çöp toplamayı çalıştırma süresine zorlanmasını da sağlayabilirsiniz. Bu, çöp toplamanın her zaman geri aramadan önce oluşmasını sağlayarak çöp toplama tarafından ortaya çıkan belirsizliği ortadan kaldırır. Hangi temsilcinin toplandığını bildiğinizde, mareşal olarak yönetilmeyen işlev işaretçisinin ömrü boyunca yönetilen taraftaki temsilciye bir başvuru tutmak için kodunuzu değiştirin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma Süresi üzerindeki etkisi  
 Temsilciler işlev işaretçisi olarak marshaled olduğunda, çalışma zamanı yönetilmeyen den yönetilen geçiş yapan bir thunk ayırır. Bu thunk, yönetilen temsilci sonunda çağrılmadan önce yönetilmeyen kodun gerçekte çağırdığı şeydir. `callbackOnCollectedDelegate` MDA etkin olmadan, temsilci toplandığında yönetilmeyen mareşal kodu silinir. `callbackOnCollectedDelegate` MDA etkinleştirildiğinde, yönetilmeyen mareşalkodu temsilci toplandığında hemen silinmez. Bunun yerine, son 1.000 örnek varsayılan olarak canlı tutulur ve çağrıldığında MDA etkinleştirmek için değiştirilir. Thunk, 1.001 mareşal delege daha toplandıktan sonra silinir.  
  
## <a name="output"></a>Çıktı  
 MDA, yönetilmeyen işlev işaretçisi üzerinde geri arama girişiminde bulunulmadan önce toplanan temsilcinin türünü bildirir.  
  
## <a name="configuration"></a>Yapılandırma  
 Aşağıdaki örnekte uygulama yapılandırma seçenekleri gösterilmektedir. MDA'nın hayatta tuttuğu thunk sayısını 1500'e ayarlıyor. Varsayılan `listSize` değer 1.000, en az 50 ve en büyük değer 2.000'dir.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bu MDA'yı etkinleştirebilecek bir durumu gösterir:  
  
```cpp
// Library.cpp : Defines the unmanaged entry point for the DLL application.  
#include "windows.h"  
#include "stdio.h"  
  
void (__stdcall *g_pfTarget)();  
  
void __stdcall Initialize(void __stdcall pfTarget())  
{  
    g_pfTarget = pfTarget;  
}  
  
void __stdcall Callback()  
{  
    g_pfTarget();  
}
```

```csharp
// C# Client  
using System;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public delegate void DCallback();  
  
    public static void Main()  
    {  
        new Entry();  
        Initialize(Target);  
        GC.Collect();  
        GC.WaitForPendingFinalizers();  
        Callback();  
    }  
  
    public static void Target()  
    {
    }  
  
    [DllImport("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Initialize(DCallback pfDelegate);  
  
    [DllImport ("Library", CallingConvention = CallingConvention.StdCall)]  
    public static extern void Callback();  
  
    ~Entry() { Console.Error.WriteLine("Entry Collected"); }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma Hazırlama](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
