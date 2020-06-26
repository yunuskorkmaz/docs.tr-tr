---
title: callbackOnCollectedDelegate MDA
description: .NET 'teki callbackOnCollectedDelegate yönetilen hata ayıklama Yardımcısı 'nı (MDA) inceleyerek, temsilci atık toplandıktan sonra bir geri çağırma gerçekleşiyorsa çağrılır.
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
ms.openlocfilehash: 32f02a4e65455f11f3bfa9260caae8b4e48f494e
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85416037"
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate MDA
`callbackOnCollectedDelegate`Yönetilen hata ayıklama Yardımcısı (MDA), bir temsilci yönetilen 'den yönetilmeyen koda bir işlev işaretçisi olarak sıralanırsa ve temsilci atık toplandıktan sonra bu işlev işaretçisine bir geri çağırma yerleştirildiğinde etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Yönetilen temsilcilerden alınan işlev işaretçileri aracılığıyla yönetilen koda çağrı yapmaya çalışırken erişim ihlalleri oluşur. Bu hatalar, ortak dil çalışma zamanı (CLR) hataları olmadığı sürece, erişim ihlali CLR kodunda gerçekleştiği için gibi görünebilir.  
  
 Hata tutarlı değil; Bazen işlev işaretçisindeki çağrı başarılı olur ve bazen başarısız olur. Hata yalnızca ağır yük altında ya da rastgele sayıda girişimde bulunabilir.  
  
## <a name="cause"></a>Nedeni  
 İşlev işaretçisinin oluşturulduğu ve yönetilmeyen koda açık olan temsilci atık olarak toplandı. Yönetilmeyen bileşen işlev işaretçisi üzerinde çağırmayı denediğinde, bir erişim ihlali oluşturur.  
  
 Çöp toplamanın ne zaman gerçekleşeceğini bağlı olduğundan hata rastgele görünür. Bir temsilci koleksiyon için uygun ise, çöp toplama işlemi geri aramadan sonra gerçekleşebilir ve çağrı başarılı olur. Diğer zamanlarda çöp toplama işlemi geri aramadan önce oluşur, geri arama bir erişim ihlali oluşturur ve program durur.  
  
 Hatanın olasılığı, işlev işaretçisindeki ve geri çağırma işleminin yanı sıra çöp koleksiyonları sıklığının sıralaması arasındaki zamana bağlıdır. Temsilciyi hazırlama ve geri çağırma işlemi arasında geçen süre kısaysa hata tek tek olur. Bu genellikle, işlev işaretçisini alan yönetilmeyen yöntemin, daha sonra kullanmak üzere işlev işaretçisini kaydetmediğini, ancak döndürmeden önce işlemini tamamlaması için hemen işlev işaretçisine geri çağırması durumunda oluşur. Benzer şekilde, bir sistem ağır yük altındayken daha fazla çöp toplama meydana gelir. Bu, geri aramadan önce çöp toplamanın gerçekleşmesinin daha büyük olmasını sağlar.  
  
## <a name="resolution"></a>Çözüm  
 Bir temsilci yönetilmeyen bir işlev işaretçisi olarak sıralandıktan sonra çöp toplayıcı ömrünü izleyemez. Bunun yerine, yönetilmeyen işlev işaretçisinin ömrü boyunca kodunuzun temsilciye bir başvuru tutması gerekir. Ancak bunu yapabilmeniz için önce hangi temsilcinin toplandığını belirlemelisiniz. MDA etkinleştirildiğinde, temsilcinin tür adını sağlar. Bu temsilciyi, bu temsilciyi yönetilmeyen koda geçiren platform çağrısı veya COM imzaları için aramak üzere kullanın. Sorunlu temsilci bu çağrı sitelerinden biri aracılığıyla geçirilir. Ayrıca, `gcUnmanagedToManaged` çalışma zamanına her geri çağırmadan önce bir çöp toplamayı zorlamak için mda ' i etkinleştirebilirsiniz. Bu, çöp toplamanın geri aramadan önce her zaman gerçekleşmesini sağlayarak çöp toplama tarafından sunulan belirsizlik kaldırır. Hangi temsilcinin toplandığını öğrendikten sonra, sıralanmış yönetilmeyen işlev işaretçisinin ömrü boyunca yönetilen tarafta bu temsilciye bir başvuru tutmak için kodunuzu değiştirin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Temsilciler işlev işaretçileri olarak sıralandığında, çalışma zamanı Yönetilmeyenden yönetilene geçişi yapan bir dönüştürücü ayırır. Bu dönüştürücü, yönetilmeyen kodun yönetilen temsilci son olarak çağrılmadan önce ne kadar çağırıldığı şeydir. `callbackOnCollectedDelegate`MDA etkin olmadan, yönetilmeyen sıralama kodu, temsilci toplandığında silinir. `callbackOnCollectedDelegate`MDA etkinleştirildikten sonra, temsilci toplandığında yönetilmeyen sıralama kodu hemen silinmez. Bunun yerine, son 1.000 örnek varsayılan olarak etkin tutulur ve çağrıldığında MDA öğesini etkinleştirmek için değiştirilir. Dönüştürücü, 1.001 daha fazla sıralanmış temsilci toplandıktan sonra silinir.  
  
## <a name="output"></a>Çıktı  
 MDA, yönetilmeyen işlev işaretçisi üzerinde bir geri çağırma yapılmadan önce toplanan temsilcinin tür adını bildirir.  
  
## <a name="configuration"></a>Yapılandırma  
 Aşağıdaki örnek, uygulama yapılandırma seçeneklerini gösterir. MDA 'ın 1.500 olarak etkin kalmasını sağlar dönüştürücüler sayısını ayarlar. Varsayılan `listSize` değer 1.000, en az 50, en fazla ise 2.000.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bu MDA ' i etkinleştirebilecek bir durum gösterilmektedir:  
  
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
