---
title: Jıtcompilationstart yönetilen hata ayıklama Yardımcısı (MDA)
description: Tam zamanında (JıT) derleyici bir .NET işlevini derlemeye başladığında, Jıtcompilationstart yönetilen hata ayıklama Yardımcısı (MDA) raporları.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 13e20c1a940b7bfa777245ba35f3cc1b003d15b2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325527"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="f6053-103">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="f6053-103">jitCompilationStart MDA</span></span>

<span data-ttu-id="f6053-104">`jitCompilationStart`Yönetilen hata ayıklama Yardımcısı (MDA), Just-In-Time (JIT) derleyicisi bir işlevi derlemeye başladığında raporlamak için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f6053-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f6053-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="f6053-105">Symptoms</span></span>  
 <span data-ttu-id="f6053-106">Çalışma kümesi boyutu, zaten yerel görüntü biçiminde olan bir program için artar, çünkü mscorjit.dll işleme yüklenir.</span><span class="sxs-lookup"><span data-stu-id="f6053-106">The working set size increases for a program that's already in native image format, because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f6053-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="f6053-107">Cause</span></span>  
<span data-ttu-id="f6053-108">Programın bağımlı olduğu tüm derlemeler yerel biçimde üretilmez veya bir derleme doğru şekilde kaydedilmemiş.</span><span class="sxs-lookup"><span data-stu-id="f6053-108">Not all the assemblies the program depends on have been generated into native format, or an assembly is not registered correctly.</span></span>  

## <a name="resolution"></a><span data-ttu-id="f6053-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="f6053-109">Resolution</span></span>  
 <span data-ttu-id="f6053-110">Bu MDA ' ın etkinleştirilmesi, hangi işlevin JıT olarak derlendiğini tanımlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6053-110">Enabling this MDA allows you to identify which function is being JIT-compiled.</span></span> <span data-ttu-id="f6053-111">İşlevi içeren derlemenin yerel biçimde oluşturulduğundan ve doğru şekilde kaydedildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="f6053-111">Make sure that the assembly that contains the function is generated to native format and properly registered.</span></span>
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f6053-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="f6053-112">Effect on the runtime</span></span>  
 <span data-ttu-id="f6053-113">Bu MDA, bir yöntem JıT derlenmeden hemen önce bir ileti günlüğe kaydedilir, bu nedenle bu MDA 'ın etkinleştirilmesi performansı önemli ölçüde etkiler.</span><span class="sxs-lookup"><span data-stu-id="f6053-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="f6053-114">Bir yöntem satır içi ise, bu MDA ayrı bir ileti oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="f6053-114">If a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f6053-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="f6053-115">Output</span></span>  
 <span data-ttu-id="f6053-116">Aşağıdaki kod örneği, örnek çıktıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6053-116">The following code sample shows sample output.</span></span> <span data-ttu-id="f6053-117">Bu durumda, çıkış, derleme testinde, "ns2.CO" sınıfındaki "d" yönteminin JıT olarak derlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6053-117">In this case, the output shows that, in assembly Test, the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="f6053-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="f6053-118">Configuration</span></span>  
 <span data-ttu-id="f6053-119">Aşağıdaki yapılandırma dosyasında, ilk JıT derlenmiş olduğunda hangi yöntemlerin raporlanacağı filtreleneceği için kullanılabilecek çeşitli filtreler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6053-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="f6053-120">Ad özniteliğinin değerini olarak ayarlayarak tüm yöntemlerin rapor olduğunu belirtebilirsiniz \* .</span><span class="sxs-lookup"><span data-stu-id="f6053-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f6053-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6053-121">Example</span></span>  
 <span data-ttu-id="f6053-122">Aşağıdaki kod örneği, önceki yapılandırma dosyası ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f6053-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6053-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6053-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f6053-124">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="f6053-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f6053-125">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="f6053-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
