---
title: jitCompilationStart MDA
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 9cae942bc01e9263720dbfe9acfb21bbb70bc548
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216252"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="c8e57-102">jitCompilationStart MDA</span><span class="sxs-lookup"><span data-stu-id="c8e57-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="c8e57-103">`jitCompilationStart` yönetilen hata ayıklama Yardımcısı (MDA), Just-In-Time (JıT) derleyicisi bir işlevi derlemeye başladığında raporlamak için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="c8e57-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="c8e57-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="c8e57-104">Symptoms</span></span>  
 <span data-ttu-id="c8e57-105">Çalışma kümesi boyutu, zaten yerel görüntü biçiminde olan bir program için artar, çünkü mscorjıt. dll işleme içine yüklendi.</span><span class="sxs-lookup"><span data-stu-id="c8e57-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="c8e57-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="c8e57-106">Cause</span></span>  
 <span data-ttu-id="c8e57-107">Programın bağımlı olduğu tüm derlemeler yerel biçimde üretilmez veya doğru kaydedilmemiş olanlardır.</span><span class="sxs-lookup"><span data-stu-id="c8e57-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="c8e57-108">Çözüm</span><span class="sxs-lookup"><span data-stu-id="c8e57-108">Resolution</span></span>  
 <span data-ttu-id="c8e57-109">Bu MDA ' ın etkinleştirilmesi, hangi işlevin JıT olarak derlendiğini belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8e57-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="c8e57-110">İşlevi içeren derlemenin yerel biçimde oluşturulup oluşturulmayacağını ve düzgün şekilde kaydedildiğini belirleme.</span><span class="sxs-lookup"><span data-stu-id="c8e57-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="c8e57-111">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="c8e57-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="c8e57-112">Bu MDA, bir yöntem JıT derlenmeden hemen önce bir ileti günlüğe kaydedilir, bu nedenle bu MDA 'ın etkinleştirilmesi performansı önemli ölçüde etkiler.</span><span class="sxs-lookup"><span data-stu-id="c8e57-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="c8e57-113">Bir yöntem satır içi ise, bu MDA 'ın ayrı bir ileti oluşturmayacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c8e57-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="c8e57-114">Çıktı</span><span class="sxs-lookup"><span data-stu-id="c8e57-114">Output</span></span>  
 <span data-ttu-id="c8e57-115">Aşağıdaki kod örneği, örnek çıktıyı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8e57-115">The following code sample shows sample output.</span></span> <span data-ttu-id="c8e57-116">Bu durumda çıkış, derleme testinde "ns2.CO" sınıfında "d" yönteminin JıT olarak derlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8e57-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="c8e57-117">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="c8e57-117">Configuration</span></span>  
 <span data-ttu-id="c8e57-118">Aşağıdaki yapılandırma dosyasında, ilk JıT derlenmiş olduğunda hangi yöntemlerin raporlanacağı filtreleneceği için kullanılabilecek çeşitli filtreler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c8e57-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="c8e57-119">Ad özniteliğinin değerini \*olarak ayarlayarak tüm yöntemlerin bildirilmesini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c8e57-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="c8e57-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="c8e57-120">Example</span></span>  
 <span data-ttu-id="c8e57-121">Aşağıdaki kod örneği, önceki yapılandırma dosyası ile kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c8e57-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8e57-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8e57-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="c8e57-123">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="c8e57-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c8e57-124">Birlikte Çalışma için Hazırlama</span><span class="sxs-lookup"><span data-stu-id="c8e57-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
