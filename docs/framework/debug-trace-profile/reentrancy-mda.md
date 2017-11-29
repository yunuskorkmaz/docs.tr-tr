---
title: "yeniden giriş MDA'sı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a54a985abbc59aea0eeb46cc74560485e86b897d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="reentrancy-mda"></a>yeniden giriş MDA'sı
`reentrancy` Yönetilen hata ayıklama Yardımcısı (MDA) girişiminde durumlarda burada yerel için yönetilen kod önceki anahtardan gerçekleştirilmediği düzenli geçiş yönetilen kod Yerelden geçiş yapılırken etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Nesne yığın bozulmuş veya diğer ciddi hatalar yönetilen kod Yerelden geçiş olduğunda ortaya çıkan.  
  
 Her iki yönde yerel ve yönetilen kod arasında geçiş iş parçacığı düzenli geçiş gerçekleştirmeniz gerekir. Ancak, belirli alt düzey genişletilebilirlik noktaları Vektörlü özel durum işleyici gibi işletim sistemi yerel koda düzenli geçiş yapmadan yönetilen anahtarlardan izin verir.  Bu anahtarlar, işletim sistemi denetimindeki yerine, ortak dil çalışma zamanı (CLR) denetimi altında şunlardır.  Bu genişletilebilirlik noktaları içinde yürüten yerel kod yönetilen kodu geri çağırma kaçınmalısınız.  
  
## <a name="cause"></a>Sebep  
 Yönetilen kod yürütülürken Vektörlü özel durum işleyici gibi bir alt düzey işletim sistemi genişletilebilirlik noktası etkinleştirdi.  Bu genişletilebilirlik noktası aracılığıyla çağrılır uygulama kodu geri yönetilen koda çağrı çalışıyor.  
  
 Bu sorun uygulama kodu tarafından her zaman kaynaklanır.  
  
## <a name="resolution"></a>Çözüm  
 Bu MDA etkinleştirdi iş parçacığı için yığın izlemesi inceleyin.  İş parçacığı yasadışı yönetilen koda çağrı çalışıyor.  Yığın izleme, bu genişletilebilirlik noktasını kullanarak uygulama kodu, bu genişletilebilirlik noktasıdır işletim sistemi kodu ve genişletilebilirlik noktası tarafından kesildi yönetilen kod ortaya çıkarır.  
  
 Örneğin, yönetilen koddan Vektörlü özel durum işleyicisi içine çağrı girişimi etkinleştirilmiş MDA görürsünüz.  İşletim sistemi özel durum kodu ve bir özel durum harekete gibi bazı yönetilen kod işleme göreceğiniz yığında bir <xref:System.DivideByZeroException> veya bir <xref:System.AccessViolationException>.  
  
 Bu örnekte, doğru çözünürlüğü Vektörlü özel durum işleyici tamamen yönetilmeyen kodunda uygulamaktır.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA CLR üzerinde etkisi yoktur.  
  
## <a name="output"></a>Çıkış  
 Geçersiz yeniden giriş yapılmaya çalışılan MDA bildirir.  Bu neden olmuyor ve sorunun nasıl giderileceği belirlemek için iş parçacığının yığın inceleyin. Örnek çıktı verilmiştir.  
  
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
 Aşağıdaki kod örneği neden bir <xref:System.AccessViolationException> oluşturulmasına.  Vektörlü özel durum işleme destekleyen Windows sürümlerinde bu çağrılacak yönetilen Vektörlü özel durum işleyici neden olur.  Varsa `reentrancy` MDA etkinleştirildiğinde, MDA denenen çağrı sırasında etkinleşir `MyHandler` destek kod işleme işletim sisteminin Vektörlü özel durum.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen hata ayıklama Yardımcıları ile hataları tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
