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
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="97fdc-102">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="97fdc-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="97fdc-103">`jitCompilationStart` Yönetilen hata ayıklama Yardımcısı (MDA) bir işlev derlemek tam zamanında (JIT) derleyici başladığında, rapor için etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="97fdc-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="97fdc-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="97fdc-104">Symptoms</span></span>  
 <span data-ttu-id="97fdc-105">Çalışan boyutu artar mscorjit.dll işlemine yüklendiği yerel görüntü biçiminde zaten bir program için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="97fdc-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="97fdc-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="97fdc-106">Cause</span></span>  
 <span data-ttu-id="97fdc-107">Program bağımlı tüm derlemeler yerel biçimine oluşturulmuş veya olan doğru kayıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="97fdc-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="97fdc-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="97fdc-108">Resolution</span></span>  
 <span data-ttu-id="97fdc-109">Bu MDA etkinleştirme JIT derlenmiş hangi işlevi belirlemenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="97fdc-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="97fdc-110">İşlevi içeren derlemenin oluşturulan yerel biçimi ve düzgün şekilde kayıtlı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="97fdc-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="97fdc-111">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="97fdc-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="97fdc-112">Bu MDA etkinleştirme önemli performans üzerinde etkisi için yalnızca bir yöntem JIT derlenmiş önce bu MDA bir ileti kaydeder.</span><span class="sxs-lookup"><span data-stu-id="97fdc-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="97fdc-113">Satır içi bir yöntem ise, bu MDA ayrı bir ileti oluşturmaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="97fdc-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="97fdc-114">Çıkış</span><span class="sxs-lookup"><span data-stu-id="97fdc-114">Output</span></span>  
 <span data-ttu-id="97fdc-115">Aşağıdaki kod örneği, örnek çıktı gösterir.</span><span class="sxs-lookup"><span data-stu-id="97fdc-115">The following code sample shows sample output.</span></span> <span data-ttu-id="97fdc-116">Bu durumda Test sınıfı "ns2.CO" üzerindeki "m" yöntemi, derlemesindeki çıktısında JIT derlenmiş.</span><span class="sxs-lookup"><span data-stu-id="97fdc-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="97fdc-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="97fdc-117">Configuration</span></span>  
 <span data-ttu-id="97fdc-118">Aşağıdaki yapılandırma dosyası, hangi yöntemlerin bildirilen ilk JIT derlenmiş olduklarında filtrelemek için işe filtreleri çeşitli gösterir.</span><span class="sxs-lookup"><span data-stu-id="97fdc-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="97fdc-119">Tüm yöntemleri için adı özniteliğinin değeri ayarlayarak bildirilmesini belirtebilirsiniz *.</span><span class="sxs-lookup"><span data-stu-id="97fdc-119">You can specify that all methods be reported by setting the value of the name attribute to *.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="97fdc-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="97fdc-120">Example</span></span>  
 <span data-ttu-id="97fdc-121">Aşağıdaki kod örneği, önceki yapılandırma dosyası ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="97fdc-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="97fdc-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97fdc-122">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="97fdc-123">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="97fdc-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="97fdc-124">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="97fdc-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
