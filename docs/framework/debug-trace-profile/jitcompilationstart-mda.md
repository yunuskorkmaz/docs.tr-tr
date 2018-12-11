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
ms.openlocfilehash: d73c299231a588a5ae0b252dd2b5a0a834685f2d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150673"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="89093-102">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="89093-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="89093-103">`jitCompilationStart` Yönetilen hata ayıklama Yardımcısı (MDA), rapora etkinleştirilirse, just-in-time (JIT) derleyici bir işlevi derlemeye yürütülmeye başladığı zaman.</span><span class="sxs-lookup"><span data-stu-id="89093-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="89093-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="89093-104">Symptoms</span></span>  
 <span data-ttu-id="89093-105">Çalışan boyutu arttıkça mscorjit.dll işlem içine yüklenmiş olduğundan, yerel görüntü biçiminde olan bir program için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="89093-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="89093-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="89093-106">Cause</span></span>  
 <span data-ttu-id="89093-107">Programa bağımlı tüm bütünleştirilmiş kodları yerel biçiminde oluşturulmuş veya sahip doğru şekilde kaydedilmemiş.</span><span class="sxs-lookup"><span data-stu-id="89093-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="89093-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="89093-108">Resolution</span></span>  
 <span data-ttu-id="89093-109">Bu MDA etkinleştirme JIT olarak derlenmiş hangi işlevi belirlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="89093-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="89093-110">İşlevi içeren bütünleştirilmiş kodun yerel biçiminde oluşturulur ve düzgün şekilde kayıtlı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="89093-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="89093-111">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="89093-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="89093-112">Bu MDA, bu MDA etkinleştirme performansı üzerinde önemli bir etkisi yoktur, dolayısıyla yalnızca bir yöntem JIT olarak derlenmiş, önce bir ileti kaydeder.</span><span class="sxs-lookup"><span data-stu-id="89093-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="89093-113">Satır içi bir yöntem ise bu mda'nın ayrı bir ileti oluşturmaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="89093-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="89093-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="89093-114">Output</span></span>  
 <span data-ttu-id="89093-115">Aşağıdaki kod örneği, örnek çıktı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="89093-115">The following code sample shows sample output.</span></span> <span data-ttu-id="89093-116">Bu durumda, "ns2.CO" sınıfı "m" metodunda Test derlemesindeki çıkışın gösterdiği JIT olarak derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="89093-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="89093-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="89093-117">Configuration</span></span>  
 <span data-ttu-id="89093-118">Aşağıdaki yapılandırma dosyası, hangi yöntemlerin JIT olarak derlenmiş olsalar ilk raporlanır filtrelemek üzere kullanılan filtreler çeşitli gösterir.</span><span class="sxs-lookup"><span data-stu-id="89093-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="89093-119">Tüm yöntemleri ad özniteliğini ayarlayarak bildirilmesini belirtebilirsiniz \*.</span><span class="sxs-lookup"><span data-stu-id="89093-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="89093-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="89093-120">Example</span></span>  
 <span data-ttu-id="89093-121">Aşağıdaki kod örneği, önceki yapılandırma dosyası ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="89093-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89093-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="89093-122">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="89093-123">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="89093-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="89093-124">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="89093-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
