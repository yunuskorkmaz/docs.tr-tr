---
title: yeniden giriş MDA'sı
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged code, debugging
- transitioning threads unmanaged to managed code
- reentrancy MDA
- reentrancy without an orderly transition
- managed debugging assistants (MDAs), reentrancy
- illegal reentrancy
- MDAs (managed debugging assistants), reentrancy
- threading [.NET Framework], managed debugging assistants
- managed code, debugging
- native debugging, MDAs
ms.assetid: 7240c3f3-7df8-4b03-bbf1-17cdce142d45
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7de0a869925816da6df8f17e14ab92964aec8d11
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094222"
---
# <a name="reentrancy-mda"></a>yeniden giriş MDA'sı
`reentrancy` Girişiminde durumlarda burada yönetilen yerel kod önceki bir geçiş gerçekleştirilmediği düzenli bir geçiş yönetilen kod Yerelden geçiş yapıldığında yönetilen hata ayıklama Yardımcısı (MDA) etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Nesne yığını bozuk ya da diğer önemli hataları yönetilen koda yerel'den geçiş sırasında gerçekleşiyor.  
  
 Herhangi bir yönde yerel ve yönetilen kod arasında geçiş iş parçacıkları düzenli geçiş gerçekleştirmeniz gerekir. Ancak, belirli alt düzey genişletilebilirlik noktaları işletim sistemindeki Vektörlü özel durum işleyicisi gibi düzenli geçiş yapmadan yerel kod için yönetilen anahtarları izin verir.  Bu anahtarlar, ortak dil çalışma zamanı (CLR) denetimi altında değil, işletim sistemi denetimi altında şunlardır.  Bu genişletilebilirlik noktaları içinde yürütülen herhangi bir yerel kod yönetilen koda geri çağırma kaçınmalısınız.  
  
## <a name="cause"></a>Sebep  
 Yönetilen kod yürütülürken Vektörlü özel durum işleyicisi gibi bir alt düzey işletim sistemi genişletilebilirlik noktası etkinleştirdi.  Uygulama kodu bu genişletilebilirlik noktası üzerinden çağrılan geri yönetilen koda çağrı çalışıyor.  
  
 Bu sorun, uygulama kodu tarafından her zaman kaynaklanır.  
  
## <a name="resolution"></a>Çözüm  
 Bu mda'nın etkinleştirilmiş iş parçacığı için yığın izlemesi inceleyin.  İş parçacığı yasadışı yönetilen koda çağrı çalışıyor.  Yığın izleme, bu genişletilebilirlik noktası kullanarak uygulama kodu, işletim sistemi kodu, bu genişletilebilirlik noktası sağlar ve genişletilebilirlik noktası tarafından kesildi yönetilen kodu ortaya.  
  
 Örneğin, bir Vektörlü özel durum işleyicisi içindeki yönetilen koddan çağırmak girişimi etkinleştirilmiş MDA görürsünüz.  İşletim sistemi özel durum kodu ve bazı yönetilen kodu gibi bir özel durum harekete işleme göreceğiniz yığında bir <xref:System.DivideByZeroException> veya <xref:System.AccessViolationException>.  
  
 Bu örnekte, doğru çözüm Vektörlü özel durum işleyicisi tamamen yönetilmeyen kodda uygulamaktır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı üzerindeki etkisi  
 Bu mda'nın CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Geçersiz yeniden giriş yapılmaya çalışılan MDA bildirir.  Bu neden oluyor ve sorunun nasıl giderileceği belirlemek için iş parçacığı yığınının inceleyin. Örnek çıktı verilmiştir.  
  
```  
Additional Information: Attempting to call into managed code without   
transitioning out first.  Do not attempt to run managed code inside   
low-level native extensibility points. Managed Debugging Assistant   
'Reentrancy' has detected a problem in 'D:\ConsoleApplication1\  
ConsoleApplication1\bin\Debug\ConsoleApplication1.vshost.exe'.  
```  
  
## <a name="configuration"></a>Yapılandırma  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reentrancy />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği neden bir <xref:System.AccessViolationException> oluşturulması için.  Vektörlü özel durum işleme destekleyen Windows sürümlerinde bu Vektörlü yönetilen özel durum işleyici çağrılması neden olur.  Varsa `reentrancy` MDA etkinleştirildiğinde, denenen çağrı sırasında MDA etkinleştirmesi `MyHandler` destek kodunu işleme işletim sisteminin Vektörlü özel durumdan.  
  
```csharp
using System;  
public delegate int ExceptionHandler(IntPtr ptrExceptionInfo);  
  
public class Reenter   
{  
    public static ExceptionHandler keepAlive;  
  
    [System.Runtime.InteropServices.DllImport("kernel32", ExactSpelling=true,   
        CharSet=System.Runtime.InteropServices.CharSet.Auto)]  
    public static extern IntPtr AddVectoredExceptionHandler(int bFirst,   
        ExceptionHandler handler);  
  
    static int MyHandler(IntPtr ptrExceptionInfo)   
    {  
        // EXCEPTION_CONTINUE_SEARCH  
        return 0;  
    }  
    void Run() {}  
  
    static void Main()   
    {  
        keepAlive = new ExceptionHandler(Reenter.MyHandler);  
        IntPtr ret = AddVectoredExceptionHandler(1, keepAlive);  
        try   
        {  
            // Dispatch on null should AV.  
            Reenter r = null;   
            r.Run();  
        }   
        catch { }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
