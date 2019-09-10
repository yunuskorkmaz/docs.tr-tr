---
title: jitCompilationStart MDA
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80473e01581a372c193c4b816a37166b73d57824
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854151"
---
# <a name="jitcompilationstart-mda"></a>jitCompilationStart MDA
`jitCompilationStart` Yönetilen hata ayıklama Yardımcısı (MDA), Just-In-Time (JIT) derleyicisi bir işlevi derlemeye başladığında raporlamak için etkinleştirilir.  
  
## <a name="symptoms"></a>Belirtiler  
 Çalışma kümesi boyutu, zaten yerel görüntü biçiminde olan bir program için artar, çünkü mscorjıt. dll işleme içine yüklendi.  
  
## <a name="cause"></a>Sebep  
 Programın bağımlı olduğu tüm derlemeler yerel biçimde üretilmez veya doğru kaydedilmemiş olanlardır.  
  
## <a name="resolution"></a>Çözüm  
 Bu MDA ' ın etkinleştirilmesi, hangi işlevin JıT olarak derlendiğini belirlemenizi sağlar. İşlevi içeren derlemenin yerel biçimde oluşturulup oluşturulmayacağını ve düzgün şekilde kaydedildiğini belirleme.  
  
## <a name="effect-on-the-runtime"></a>Çalışma zamanında etki  
 Bu MDA, bir yöntem JıT derlenmeden hemen önce bir ileti günlüğe kaydedilir, bu nedenle bu MDA 'ın etkinleştirilmesi performansı önemli ölçüde etkiler. Bir yöntem satır içi ise, bu MDA 'ın ayrı bir ileti oluşturmayacağını unutmayın.  
  
## <a name="output"></a>Çıkış  
 Aşağıdaki kod örneği, örnek çıktıyı gösterir. Bu durumda çıkış, derleme testinde "ns2.CO" sınıfında "d" yönteminin JıT olarak derlendiğini gösterir.  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a>Yapılandırma  
 Aşağıdaki yapılandırma dosyasında, ilk JıT derlenmiş olduğunda hangi yöntemlerin raporlanacağı filtreleneceği için kullanılabilecek çeşitli filtreler gösterilmektedir. Ad özniteliğinin değerini olarak \*ayarlayarak tüm yöntemlerin rapor olduğunu belirtebilirsiniz.  
  
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
  
```csharp
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Birlikte Çalışma için Hazırlama](../../../docs/framework/interop/interop-marshaling.md)
