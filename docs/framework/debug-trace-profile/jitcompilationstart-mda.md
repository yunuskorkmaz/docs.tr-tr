---
title: jitCompilationStart MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fd520392ca7f6bb97ac11d868db7a0df9a32d5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="jitcompilationstart-mda"></a>jitCompilationStart MDA
`jitCompilationStart` Yönetilen hata ayıklama Yardımcısı (MDA) bir işlev derlemek tam zamanında (JIT) derleyici başladığında, rapor için etkinleştirildi.  
  
## <a name="symptoms"></a>Belirtiler  
 Çalışan boyutu artar mscorjit.dll işlemine yüklendiği yerel görüntü biçiminde zaten bir program için ayarlayın.  
  
## <a name="cause"></a>Sebep  
 Program bağımlı tüm derlemeler yerel biçimine oluşturulmuş veya olan doğru kayıtlı değil.  
  
## <a name="resolution"></a>Çözüm  
 Bu MDA etkinleştirme JIT derlenmiş hangi işlevi belirlemenize olanak sağlar. İşlevi içeren derlemenin oluşturulan yerel biçimi ve düzgün şekilde kayıtlı olup olmadığını belirler.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanı etkisi  
 Bu MDA etkinleştirme önemli performans üzerinde etkisi için yalnızca bir yöntem JIT derlenmiş önce bu MDA bir ileti kaydeder. Satır içi bir yöntem ise, bu MDA ayrı bir ileti oluşturmaz unutmayın.  
  
## <a name="output"></a>Çıkış  
 Aşağıdaki kod örneği, örnek çıktı gösterir. Bu durumda Test sınıfı "ns2.CO" üzerindeki "m" yöntemi, derlemesindeki çıktısında JIT derlenmiş.  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma dosyası, hangi yöntemlerin bildirilen ilk JIT derlenmiş olduklarında filtrelemek için işe filtreleri çeşitli gösterir. Tüm yöntemleri için adı özniteliğinin değeri ayarlayarak bildirilmesini belirtebilirsiniz *.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, önceki yapılandırma dosyası ile kullanılmak üzere tasarlanmıştır.  
  
```  
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
