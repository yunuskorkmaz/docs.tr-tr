---
title: jitCompilationStart MDA
description: Just-In-Time (JıT) derleyicisi bir .NET işlevini derlemeye başladığında rapor için başlatılan Jıtcompilationstart yönetilen hata ayıklama Yardımcısı 'nı (MDA) kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: bf2d09f433f0b8e4056fecd1f4e82bf3b91dd2bc
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904136"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="17d25-103">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="17d25-103">jitCompilationStart MDA</span></span>
<span data-ttu-id="17d25-104">`jitCompilationStart`Yönetilen hata ayıklama Yardımcısı (MDA), Just-In-Time (JIT) derleyicisi bir işlevi derlemeye başladığında raporlamak için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="17d25-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="17d25-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="17d25-105">Symptoms</span></span>  
 <span data-ttu-id="17d25-106">İşleme mscorjit.dll yüklendiği için, zaten yerel görüntü biçiminde olan bir program için çalışma kümesi boyutu artar.</span><span class="sxs-lookup"><span data-stu-id="17d25-106">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="17d25-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="17d25-107">Cause</span></span>  
 <span data-ttu-id="17d25-108">Programın bağımlı olduğu tüm derlemeler yerel biçimde üretilmez veya doğru kaydedilmemiş olanlardır.</span><span class="sxs-lookup"><span data-stu-id="17d25-108">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="17d25-109">Çözüm</span><span class="sxs-lookup"><span data-stu-id="17d25-109">Resolution</span></span>  
 <span data-ttu-id="17d25-110">Bu MDA ' ın etkinleştirilmesi, hangi işlevin JıT olarak derlendiğini belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="17d25-110">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="17d25-111">İşlevi içeren derlemenin yerel biçimde oluşturulup oluşturulmayacağını ve düzgün şekilde kaydedildiğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="17d25-111">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="17d25-112">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="17d25-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="17d25-113">Bu MDA, bir yöntem JıT derlenmeden hemen önce bir ileti günlüğe kaydedilir, bu nedenle bu MDA 'ın etkinleştirilmesi performansı önemli ölçüde etkiler.</span><span class="sxs-lookup"><span data-stu-id="17d25-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="17d25-114">Bir yöntem satır içi ise, bu MDA 'ın ayrı bir ileti oluşturmayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="17d25-114">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="17d25-115">Çıkış</span><span class="sxs-lookup"><span data-stu-id="17d25-115">Output</span></span>  
 <span data-ttu-id="17d25-116">Aşağıdaki kod örneği, örnek çıktıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="17d25-116">The following code sample shows sample output.</span></span> <span data-ttu-id="17d25-117">Bu durumda çıkış, derleme testinde "ns2.CO" sınıfında "d" yönteminin JıT olarak derlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="17d25-117">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="17d25-118">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="17d25-118">Configuration</span></span>  
 <span data-ttu-id="17d25-119">Aşağıdaki yapılandırma dosyasında, ilk JıT derlenmiş olduğunda hangi yöntemlerin raporlanacağı filtreleneceği için kullanılabilecek çeşitli filtreler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="17d25-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="17d25-120">Ad özniteliğinin değerini olarak ayarlayarak tüm yöntemlerin rapor olduğunu belirtebilirsiniz \* .</span><span class="sxs-lookup"><span data-stu-id="17d25-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="17d25-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="17d25-121">Example</span></span>  
 <span data-ttu-id="17d25-122">Aşağıdaki kod örneği, önceki yapılandırma dosyası ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="17d25-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17d25-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17d25-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="17d25-124">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="17d25-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="17d25-125">Birlikte Çalışma Hazırlama</span><span class="sxs-lookup"><span data-stu-id="17d25-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
