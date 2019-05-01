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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 459465064fe9db9f2f0aebb4153a3caea173af4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61875075"
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate MDA
`callbackOnCollectedDelegate` Yönetilen hata ayıklama Yardımcısı (MDA) etkin olduğu bir temsilci gelen yönetilen ve yönetilmeyen kodu bir işlev işaretçisi olarak sıralanır ve çöp olarak toplanacak temsilci sonra bir geri çağırma, işlev işaretçisi üzerinde yerleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Erişim ihlalleri yönetilen temsilciler edinilen işlev işaretçileri aracılığıyla yönetilen koda çağrı çalışılırken oluşur. Olmayan ortak dil çalışma zamanı (CLR) hataları sırasında bu hatalar, erişim ihlali CLR kodda oluştuğu için bunu gibi görünebilir.  
  
 Hata tutarlı değil; Bazen arama işlev işaretçisi üzerinde başarılı olur ve bazen başarısız olur. Hata, ağır yük altında yalnızca veya rastgele bir deneme sayısı ortaya çıkabilir.  
  
## <a name="cause"></a>Sebep  
 Temsilci, işlev işaretçisi oluşturuldu ve yönetilmeyen kod sunulan çöp olarak toplanacak oluştu. Yönetilmeyen bileşeni çağrı işlev işaretçisi üzerinde çalıştığında, erişim ihlaline neden olur.  
  
 Çöp toplama oluştuğunda bağımlı olduğundan dolayı başarısız rastgele görünür. Koleksiyon için bir temsilci uygunsa, çöp toplama geri çağırma sonra ortaya çıkabilir ve çağrının başarılı. Diğer zamanlarda, çöp toplama geri çağırma önce oluşur, geri çağırma erişim ihlaline neden olur ve program durdurur.  
  
 Temsilci ve geri arama işlev işaretçisi yanı sıra atık Toplamaların sıklığını hazırlama arasındaki zaman hata olasılığını bağlıdır. Temsilci ve erişilemez geri çağırma hazırlama arasındaki zaman kısa ise, ara sıra hatasıdır. Bu genellikle işlev işaretçisi alma yönetilmeyen yöntemi daha sonra kullanmak için işlev işaretçisi kaydettiğinizde değil ancak bunun yerine geri dönmeden önce bu işlemi hemen tamamlanması işlev işaretçisi çağırır karşılaşılan bir durumdur. Benzer şekilde, bir sistem daha olası bir çöp toplama geri çağırma önce meydana gelir getiren ağır yük altında olduğunda daha fazla çöp koleksiyonlarının meydana geldiği.  
  
## <a name="resolution"></a>Çözüm  
 Bir temsilci çıkış bir yönetilmeyen işlev işaretçisi sıralanmış sonra atık toplayıcı ömrü izleyemezsiniz. Bunun yerine, kodunuzu temsilci bir başvuru yönetilmeyen işlev işaretçisi ömrü boyunca tutmanız gerekir. Ancak bunu yapmadan önce öncelikle hangi temsilci toplanan belirlemeniz gerekir. MDA etkinleştirildiğinde, temsilci türünün adı sağlar. Kodunuz için platform çağırma arama ya da bu temsilciyi yönetilmeyen koda geçirebilirsiniz COM imzaları bu adı kullanın. Bunlardan biri geçirilir sorunlu temsilci çağrı siteleri. Ayrıca etkinleştirebilirsiniz `gcUnmanagedToManaged` zamanına her geri çağırma önce bir Çöp toplamayı zorlamak için MDA. Bu geri çağırma önce her zaman bir çöp toplama oluşan sağlayarak çöp toplama tarafından tanıtılan belirsizlik kaldırır. Hangi temsilci toplanan öğrendikten sonra bu temsilci bir başvuru yönetilen tarafında sıralanmış yönetilmeyen işlev işaretçisi ömrü boyunca saklamak için kodunuzu değiştirin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 İşlev işaretçileri olarak temsilciler başvuruya çalışma zamanı yönetilmeyen yönetilene geçiş yapan bir dönüştürücü ayırır. Bu dönüştürücü ne yönetilmeyen kod gerçekten yönetilen önce çağırır olan temsilci son çağrılır. Olmadan `callbackOnCollectedDelegate` MDA etkin, temsilci toplanan yönetilmeyen sıralama kodu silinir. İle `callbackOnCollectedDelegate` MDA etkin, temsilci toplanan olduğunda yönetilmeyen sıralama kodu hemen silinmez. Bunun yerine, en son 1.000 örnekleri varsayılan olarak Canlı tutulur ve çağrıldığında MDA etkinleştirmek için değiştirildi. Dönüştürücü, sonunda 1,001 daha sıralanmış temsilciler toplanan sonra silinir.  
  
## <a name="output"></a>Çıkış  
 MDA, bir geri çağırma girişiminde bulunuldu önce kendi yönetilmeyen işlev işaretçisini toplanan temsilci türü adını bildirir.  
  
## <a name="configuration"></a>Yapılandırma  
 Aşağıdaki örnek, uygulama yapılandırma seçeneklerini gösterir. Dönüştürücüler 1,500 için MDA etkin tutar sayısını ayarlar. Varsayılan `listSize` 2.000 en yüksek değer değer 1000'dir ve en az 50'dir.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bu mda'nın etkinleştirebilirsiniz bir durumu gösterir:  
  
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
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
- [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
