---
title: openGenericCERCall MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
ms.openlocfilehash: 7492a4c0547680a6ace85a5f7c98567770f5575a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181774"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="e55f9-102">openGenericCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="e55f9-102">openGenericCERCall MDA</span></span>

<span data-ttu-id="e55f9-103">Yönetilen `openGenericCERCall` hata ayıklama yardımcısı, kök yönteminde genel tür değişkenleri içeren kısıtlanmış bir yürütme bölgesi (CER) grafiğinin JIT derlemeveya yerel görüntü oluşturma zamanında işlendiğini ve genel tür değişkenlerinden en az birinin nesne başvuru türü olduğu konusunda uyarmak için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e55f9-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>

## <a name="symptoms"></a><span data-ttu-id="e55f9-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="e55f9-104">Symptoms</span></span>

<span data-ttu-id="e55f9-105">Cer kodu, iş parçacığı iptal edildiğinde veya uygulama etki alanı boşaltıldığında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="e55f9-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>

## <a name="cause"></a><span data-ttu-id="e55f9-106">Nedeni</span><span class="sxs-lookup"><span data-stu-id="e55f9-106">Cause</span></span>

<span data-ttu-id="e55f9-107">JIT derleme zamanında, bir nesne başvuru türü içeren bir anlık ileti yalnızca, elde edilen kod paylaşıldı ve nesne başvuru türü değişkenlerinin her biri herhangi bir nesne başvuru türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="e55f9-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="e55f9-108">Bu, bazı çalışma zamanı kaynaklarının önceden hazırlanmasını engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e55f9-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>

<span data-ttu-id="e55f9-109">Özellikle, genel tür değişkenleri ile yöntemler tembel arka planda kaynakları tahsis edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e55f9-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="e55f9-110">Bunlara genel sözlük girişleri denir.</span><span class="sxs-lookup"><span data-stu-id="e55f9-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="e55f9-111">Örneğin, genel bir `List<T> list = new List<T>();` `T` tür değişkeninin olduğu deyim için çalışma zamanı yukarı bakmalı ve muhtemelen çalışma `List<Object>, List<String>`zamanında tam anlık oluşturmayı, örneğin, ve saire.</span><span class="sxs-lookup"><span data-stu-id="e55f9-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`, and so forth.</span></span> <span data-ttu-id="e55f9-112">Bu, geliştiricinin denetimi dışında bellek tükenen çeşitli nedenlerle başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="e55f9-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>

<span data-ttu-id="e55f9-113">Bu MDA sadece JIT derleme zamanında etkinleştirilmelidir, tam bir anlık olduğunda değil.</span><span class="sxs-lookup"><span data-stu-id="e55f9-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>

<span data-ttu-id="e55f9-114">Bu MDA etkinleştirildiğinde, olası belirtiler CEO'ların kötü anlık algılamalar için işlevsel olmadığıdır.</span><span class="sxs-lookup"><span data-stu-id="e55f9-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="e55f9-115">Aslında, çalışma süresi MDA'nın etkinleştirilmesine neden olan koşullar altında bir CER uygulamaya çalışmamıştır.</span><span class="sxs-lookup"><span data-stu-id="e55f9-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="e55f9-116">Bu nedenle, geliştirici CER'in paylaşılan bir anlık iletisini kullanırsa, JIT derleme hataları, genel yazı yükleme hataları veya amaçlanan CER bölgesindeki iş parçacığı iptalleri yakalanmaz.</span><span class="sxs-lookup"><span data-stu-id="e55f9-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>

## <a name="resolution"></a><span data-ttu-id="e55f9-117">Çözüm</span><span class="sxs-lookup"><span data-stu-id="e55f9-117">Resolution</span></span>

<span data-ttu-id="e55f9-118">CER içerebilecek yöntemler için nesne başvuru türüne ait genel tür değişkenleri kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e55f9-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="e55f9-119">Çalışma Süresi üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="e55f9-119">Effect on the Runtime</span></span>

<span data-ttu-id="e55f9-120">Bu MDA'nın CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="e55f9-120">This MDA has no effect on the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="e55f9-121">Çıktı</span><span class="sxs-lookup"><span data-stu-id="e55f9-121">Output</span></span>

<span data-ttu-id="e55f9-122">Bu MDA çıktısının bir örneği aşağıda veda edilebistir:</span><span class="sxs-lookup"><span data-stu-id="e55f9-122">The following is a sample of output from this MDA:</span></span>
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution.
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a><span data-ttu-id="e55f9-123">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e55f9-123">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <openGenericCERCall/>
  </assistants>
</mdaConfig>
```  

## <a name="example"></a><span data-ttu-id="e55f9-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e55f9-124">Example</span></span>

<span data-ttu-id="e55f9-125">CER kodu yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="e55f9-125">The CER code is not executed.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.CompilerServices;

class Program
{
    static void Main(string[] args)
    {
        CallGenericMethods();
    }
    static void CallGenericMethods()
    {
        // This call is correct. The instantiation of the method
        // contains only nonreference types.
        MyClass.GenericMethodWithCer<int>();

        // This call is incorrect. A shared version of the method that
        // cannot be completely analyzed will be JIT-compiled. The
        // MDA will be activated at JIT-compile time, not at run time.
        MyClass.GenericMethodWithCer<String>();
    }
}

class MyClass
{
    public static void GenericMethodWithCer<T>()
    {
        RuntimeHelpers.PrepareConstrainedRegions();
        try
        {

        }
        finally
        {
            // This is the start of the CER.
            Console.WriteLine("In finally block.");
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="e55f9-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e55f9-126">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="e55f9-127">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="e55f9-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
