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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44b6ee3e4f74a523c1e902a4eb48a64b11eb3937
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2019
ms.locfileid: "72960910"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="3b0d5-102">openGenericCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="3b0d5-102">openGenericCERCall MDA</span></span>

<span data-ttu-id="3b0d5-103">`openGenericCERCall` yönetilen hata ayıklama Yardımcısı, kök yöntemde genel tür değişkenleri olan kısıtlanmış bir yürütme bölgesi (CER) grafiğinin JıT derleme veya yerel görüntü oluşturma zamanı ve en az bir genel türden işlendiği konusunda uyarma için etkinleştirilir. değişkenler bir nesne başvuru türüdür.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>

## <a name="symptoms"></a><span data-ttu-id="3b0d5-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="3b0d5-104">Symptoms</span></span>

<span data-ttu-id="3b0d5-105">Bir iş parçacığı iptal edildiğinde veya bir uygulama etki alanı kaldırıldığında CER kodu çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>

## <a name="cause"></a><span data-ttu-id="3b0d5-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="3b0d5-106">Cause</span></span>

<span data-ttu-id="3b0d5-107">JıT derleme zamanında, bir nesne başvuru türü içeren bir örnekleme yalnızca temsilcisidir çünkü sonuç kodu paylaşılır ve nesne başvuru türü değişkenlerinin her biri herhangi bir nesne başvuru türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="3b0d5-108">Bu, bazı çalışma zamanı kaynaklarının zamandan önce hazırlanmasını engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>

<span data-ttu-id="3b0d5-109">Özellikle, genel tür değişkenlerine sahip Yöntemler geç kaynak ayırmayı arka planda alabilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="3b0d5-110">Bunlar genel sözlük girdileri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="3b0d5-111">Örneğin, `T` bir genel tür değişkeni olan deyimin `List<T> list = new List<T>();`, çalışma zamanının, örneğin `List<Object>, List<String>`, vb. çalışma zamanında tam olarak örneğini oluşturması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`, and so forth.</span></span> <span data-ttu-id="3b0d5-112">Bu, geliştirici denetiminin ötesinde bellek tükenme gibi çeşitli nedenlerle başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>

<span data-ttu-id="3b0d5-113">Bu MDA, tam bir örnek oluşturma işlemi olmadığında değil, yalnızca JıT derleme sırasında etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>

<span data-ttu-id="3b0d5-114">Bu MDA etkinleştirildiğinde, büyük ihtimalle CERs kötü örneklemelerde işlevsel değildir.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="3b0d5-115">Aslında, çalışma zamanı, MDA 'ın etkinleştirilmesini neden olan koşullarda bir CER uygulamayı denemedi.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="3b0d5-116">Böylece geliştirici, CER 'nin paylaşılan bir örneklemesini kullanıyorsa JıT derleme hataları, genel türler türü yükleme hataları veya hedeflenen CER bölgesi dahilinde iş parçacığı durdurulduğunda yakalanmaz.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>

## <a name="resolution"></a><span data-ttu-id="3b0d5-117">Çözüm</span><span class="sxs-lookup"><span data-stu-id="3b0d5-117">Resolution</span></span>

<span data-ttu-id="3b0d5-118">Bir CER içerebilen yöntemler için nesne başvuru türü olan genel tür değişkenlerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="3b0d5-119">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="3b0d5-119">Effect on the Runtime</span></span>

<span data-ttu-id="3b0d5-120">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-120">This MDA has no effect on the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="3b0d5-121">Çıkış</span><span class="sxs-lookup"><span data-stu-id="3b0d5-121">Output</span></span>

<span data-ttu-id="3b0d5-122">Bu MDA 'ın çıkış örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3b0d5-122">The following is a sample of output from this MDA:</span></span>
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution. 
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a><span data-ttu-id="3b0d5-123">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="3b0d5-123">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <openGenericCERCall/>
  </assistants>
</mdaConfig>
```  

## <a name="example"></a><span data-ttu-id="3b0d5-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="3b0d5-124">Example</span></span>

<span data-ttu-id="3b0d5-125">CER kodu yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-125">The CER code is not executed.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3b0d5-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b0d5-126">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="3b0d5-127">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="3b0d5-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
