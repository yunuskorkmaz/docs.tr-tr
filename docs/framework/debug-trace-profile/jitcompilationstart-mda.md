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
ms.openlocfilehash: 9643a2d2ea0967b8cf6d8e18ce2e9073ae583f71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387042"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="fc55c-102">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="fc55c-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="fc55c-103">`jitCompilationStart` Yönetilen hata ayıklama Yardımcısı (MDA) bir işlev derlemek tam zamanında (JIT) derleyici başladığında, rapor için etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="fc55c-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="fc55c-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="fc55c-104">Symptoms</span></span>  
 <span data-ttu-id="fc55c-105">Çalışan boyutu artar mscorjit.dll işlemine yüklendiği yerel görüntü biçiminde zaten bir program için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc55c-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="fc55c-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="fc55c-106">Cause</span></span>  
 <span data-ttu-id="fc55c-107">Program bağımlı tüm derlemeler yerel biçimine oluşturulmuş veya olan doğru kayıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="fc55c-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="fc55c-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="fc55c-108">Resolution</span></span>  
 <span data-ttu-id="fc55c-109">Bu MDA etkinleştirme JIT derlenmiş hangi işlevi belirlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc55c-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="fc55c-110">İşlevi içeren derlemenin oluşturulan yerel biçimi ve düzgün şekilde kayıtlı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="fc55c-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="fc55c-111">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="fc55c-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="fc55c-112">Bu MDA etkinleştirme önemli performans üzerinde etkisi için yalnızca bir yöntem JIT derlenmiş önce bu MDA bir ileti kaydeder.</span><span class="sxs-lookup"><span data-stu-id="fc55c-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="fc55c-113">Satır içi bir yöntem ise, bu MDA ayrı bir ileti oluşturmaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fc55c-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="fc55c-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="fc55c-114">Output</span></span>  
 <span data-ttu-id="fc55c-115">Aşağıdaki kod örneği, örnek çıktı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc55c-115">The following code sample shows sample output.</span></span> <span data-ttu-id="fc55c-116">Bu durumda Test sınıfı "ns2.CO" üzerindeki "m" yöntemi, derlemesindeki çıktısında JIT derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="fc55c-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="fc55c-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="fc55c-117">Configuration</span></span>  
 <span data-ttu-id="fc55c-118">Aşağıdaki yapılandırma dosyası, hangi yöntemlerin bildirilen ilk JIT derlenmiş olduklarında filtrelemek için işe filtreleri çeşitli gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc55c-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="fc55c-119">Tüm yöntemleri için adı özniteliğinin değeri ayarlayarak bildirilmesini belirtebilirsiniz \*.</span><span class="sxs-lookup"><span data-stu-id="fc55c-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="fc55c-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc55c-120">Example</span></span>  
 <span data-ttu-id="fc55c-121">Aşağıdaki kod örneği, önceki yapılandırma dosyası ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="fc55c-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fc55c-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc55c-122">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="fc55c-123">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="fc55c-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="fc55c-124">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="fc55c-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
