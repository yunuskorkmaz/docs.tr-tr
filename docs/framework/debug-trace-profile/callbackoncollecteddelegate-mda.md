---
title: callbackOnCollectedDelegate MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
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
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2e9f2208f2e309b2433bc158a309284131ae8abd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="callbackoncollecteddelegate-mda"></a>callbackOnCollectedDelegate MDA
`callbackOnCollectedDelegate` Yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilmiş bir temsilci gelen bir işlev işaretçisi olarak yönetilmeyen kod için yönetilen sıralanmış olduğundan ve temsilci toplanacak sağlandıktan sonra bir geri çağırma bu işlev işaretçisi yerleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Yönetilen temsilciler koleksiyonundan edinilen işlev işaretçileri aracılığıyla yönetilen koda çağrı girişimi erişim ihlalleri oluşur. Olmayan ortak dil çalışma zamanı (CLR) hataları sırasında bu hataları, erişim ihlali CLR kodunda oluştuğundan bunu görünebilir.  
  
 Hata tutarlı değil; Bazen işlev işaretçisi çağrıda başarılı ve bazen başarısız olur. Hata, ağır yük altında yalnızca veya rastgele bir deneme sayısı ortaya çıkabilir.  
  
## <a name="cause"></a>Sebep  
 Hangi işlev işaretçisi oluşturuldu ve yönetilmeyen kodundaki temsilci toplanacak oluştu. İşlev işaretçisi çağırmak yönetilmeyen bileşen çalıştığında, erişim ihlali oluşturur.  
  
 Çöp toplama oluştuğunda bağımlı olduğundan dolayı başarısız rastgele görüntülenir. Koleksiyon için bir temsilci uygunsa, çağrı başarılı ve atık toplama sonra geri çağırma oluşabilir. Diğer saatlerde atık toplama önce geri çağırma işlemi gerçekleştiğinde, erişim ihlali geri çağırma oluşturur ve programı durdurur.  
  
 Temsilci ile geri çağırma işlevi işaretçisi yanı sıra çöp koleksiyonları sıklığını hazırlama arasında geçen zamanı hata olasılığını bağlıdır. Temsilci ve olmadığını geri çağırma hazırlama arasında geçen zamanı kısaysa durumlarıyla hatasıdır. Bu genellikle işlev işaretçisi alma yönetilmeyen yöntemi, daha sonra kullanmak için işlev işaretçisi kaydetmez ancak bunun yerine geri dönmeden önce bu işlemi hemen tamamlamak için işlev işaretçisi çağırır karşılaşılan bir durumdur. Bir sistem büyük olasılıkla çöp toplama önce geri dönüş meydana gelmez kolaylaştırır ağır yük altında benzer şekilde, daha fazla çöp koleksiyonlarının meydana gelir.  
  
## <a name="resolution"></a>Çözüm  
 Bir temsilci çıkışı bir yönetilmeyen işlev işaretçisi sıralanmış sonra atık toplayıcı yaşam izleyemez. Bunun yerine, kodunuzu temsilci başvuru yönetilmeyen işlev işaretçisi ömrü boyunca tutmanız gerekir. Ancak bunu yapmadan önce ilk olarak hangi temsilci toplanan belirlemeniz gerekir. MDA etkinleştirildiğinde temsilci türü adını sağlar. Kodunuz için platform çağırma arama ya da bu temsilciyi yönetilmeyen koda geçirme COM imzaları bu adı kullanın. Sorunlu temsilci bunlardan birini geçirilen çağırma siteleri. Etkinleştirebilirsiniz `gcUnmanagedToManaged` MDA her geri çağırma önce çöp toplama çalışma zamanı içine zorla. Bu geri çağırma önce her zaman bir atık toplama oluşan sağlayarak atık toplama tarafından sunulan belirsizlik kaldırır. Hangi temsilci toplanan öğrendikten sonra bu temsilciyi başvuru yönetilen tarafında sıralanmış yönetilmeyen işlev işaretçisi ömrü boyunca tutmak için kodunuzu değiştirin.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Temsilciler işlev işaretçileri sıralanmış, çalışma zamanı yönetilmeyenden yönetilene geçiş yapan bir dönüştürücü ayırır. Bu dönüştürücü ne yönetilmeyen kod gerçekte yönetilen önce çağırır olan temsilci son olarak çağrılır. Olmadan `callbackOnCollectedDelegate` MDA etkin, temsilci toplanan olduğunda yönetilmeyen hazırlama kod silinir. İle `callbackOnCollectedDelegate` MDA etkin, temsilci toplanan olduğunda yönetilmeyen hazırlama kod hemen silinmez. Bunun yerine, en son 1.000 örnekleri varsayılan olarak Canlı tutulur ve çağrıldığında MDA etkinleştirmek için değiştirildi. 1,001 daha sıralanmış temsilciler toplanan sonra dönüştürücü sonunda silinir.  
  
## <a name="output"></a>Çıkış  
 MDA bir geri çağırma denendi önce kendi yönetilmeyen işlev işaretçisi toplanan temsilci tür adını bildirir.  
  
## <a name="configuration"></a>Yapılandırma  
 Aşağıdaki örnek uygulama yapılandırma seçeneklerini gösterir. MDA 1.500 için etkin tutar dönüştürücüler sayısını ayarlar. Varsayılan `listSize` değerdir 1.000, en az 50'dir ve 2.000 en yüksek değer.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <callbackOnCollectedDelegate listSize="1500" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bu MDA etkinleştirebilirsiniz bir durumu gösterir:  
  
```  
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
// ---------------------------------------------------  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte çalışma hazırlama](../../../docs/framework/interop/interop-marshaling.md)  
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
