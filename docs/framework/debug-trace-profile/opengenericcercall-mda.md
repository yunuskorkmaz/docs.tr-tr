---
title: openGenericCERCall MDA
description: Bir iş parçacığı iptal edildiğinde veya bir uygulama etki alanı kaldırıldığında CER kodu çalışmazsa etkinleştirebilen openGenericCERCall yönetilen hata ayıklama Yardımcısı ' na bakın.
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
ms.openlocfilehash: 4df33b0cdf9759edec47f02b3feb671d03284ec8
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803943"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="b18bd-103">openGenericCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="b18bd-103">openGenericCERCall MDA</span></span>

<span data-ttu-id="b18bd-104">`openGenericCERCall`Yönetilen hata ayıklama Yardımcısı, kök yöntemde genel tür değişkenleri olan kısıtlanmış bir yürütme bölgesi (cer) GRAFIĞININ JIT derleme veya yerel görüntü oluşturma zamanında işlendiğini ve genel tür değişkenlerinden en az birinin bir nesne başvuru türü olduğunu uyarmak için etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b18bd-104">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>

## <a name="symptoms"></a><span data-ttu-id="b18bd-105">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="b18bd-105">Symptoms</span></span>

<span data-ttu-id="b18bd-106">Bir iş parçacığı iptal edildiğinde veya bir uygulama etki alanı kaldırıldığında CER kodu çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="b18bd-106">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>

## <a name="cause"></a><span data-ttu-id="b18bd-107">Nedeni</span><span class="sxs-lookup"><span data-stu-id="b18bd-107">Cause</span></span>

<span data-ttu-id="b18bd-108">JıT derleme zamanında, bir nesne başvuru türü içeren bir örnekleme yalnızca temsilcisidir çünkü sonuç kodu paylaşılır ve nesne başvuru türü değişkenlerinin her biri herhangi bir nesne başvuru türü olabilir.</span><span class="sxs-lookup"><span data-stu-id="b18bd-108">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="b18bd-109">Bu, bazı çalışma zamanı kaynaklarının zamandan önce hazırlanmasını engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b18bd-109">This can prevent the preparation of some run-time resources ahead of time.</span></span>

<span data-ttu-id="b18bd-110">Özellikle, genel tür değişkenlerine sahip Yöntemler geç kaynak ayırmayı arka planda alabilir.</span><span class="sxs-lookup"><span data-stu-id="b18bd-110">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="b18bd-111">Bunlar genel sözlük girdileri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="b18bd-111">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="b18bd-112">Örneğin, `List<T> list = new List<T>();` `T` bir genel tür değişkeni olan, çalışma zamanının bakmalı olması ve muhtemelen çalışma zamanında (örneğin, vb.) tam örneklemeyi oluşturması gerekir `List<Object>, List<String>` .</span><span class="sxs-lookup"><span data-stu-id="b18bd-112">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`, and so forth.</span></span> <span data-ttu-id="b18bd-113">Bu, geliştirici denetiminin ötesinde bellek tükenme gibi çeşitli nedenlerle başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="b18bd-113">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>

<span data-ttu-id="b18bd-114">Bu MDA, tam bir örnek oluşturma işlemi olmadığında değil, yalnızca JıT derleme sırasında etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="b18bd-114">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>

<span data-ttu-id="b18bd-115">Bu MDA etkinleştirildiğinde, büyük ihtimalle CERs kötü örneklemelerde işlevsel değildir.</span><span class="sxs-lookup"><span data-stu-id="b18bd-115">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="b18bd-116">Aslında, çalışma zamanı, MDA 'ın etkinleştirilmesini neden olan koşullarda bir CER uygulamayı denemedi.</span><span class="sxs-lookup"><span data-stu-id="b18bd-116">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="b18bd-117">Böylece geliştirici, CER 'nin paylaşılan bir örneklemesini kullanıyorsa JıT derleme hataları, genel türler türü yükleme hataları veya hedeflenen CER bölgesi dahilinde iş parçacığı durdurulduğunda yakalanmaz.</span><span class="sxs-lookup"><span data-stu-id="b18bd-117">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>

## <a name="resolution"></a><span data-ttu-id="b18bd-118">Çözüm</span><span class="sxs-lookup"><span data-stu-id="b18bd-118">Resolution</span></span>

<span data-ttu-id="b18bd-119">Bir CER içerebilen yöntemler için nesne başvuru türü olan genel tür değişkenlerini kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b18bd-119">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="b18bd-120">Çalışma zamanında etki</span><span class="sxs-lookup"><span data-stu-id="b18bd-120">Effect on the Runtime</span></span>

<span data-ttu-id="b18bd-121">Bu MDA, CLR üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="b18bd-121">This MDA has no effect on the CLR.</span></span>

## <a name="output"></a><span data-ttu-id="b18bd-122">Çıktı</span><span class="sxs-lookup"><span data-stu-id="b18bd-122">Output</span></span>

<span data-ttu-id="b18bd-123">Bu MDA 'ın çıkış örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b18bd-123">The following is a sample of output from this MDA:</span></span>
  
 ```output
 Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.
 The caller must ensure this method is prepared explicitly at run time prior to execution.
 method name="GenericMethodWithCer"
 declaringType name="OpenGenericCERCall"
 ```

## <a name="configuration"></a><span data-ttu-id="b18bd-124">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b18bd-124">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <openGenericCERCall/>
  </assistants>
</mdaConfig>
```  

## <a name="example"></a><span data-ttu-id="b18bd-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="b18bd-125">Example</span></span>

<span data-ttu-id="b18bd-126">CER kodu yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="b18bd-126">The CER code is not executed.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b18bd-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b18bd-127">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="b18bd-128">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="b18bd-128">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
