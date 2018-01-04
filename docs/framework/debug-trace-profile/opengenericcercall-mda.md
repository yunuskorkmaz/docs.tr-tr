---
title: openGenericCERCall MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), CER calls
- open generic CER calls
- constrained execution regions
- openGenericCERCall MDA
- CER calls
- managed debugging assistants (MDAs), CER calls
- generics [.NET Framework], open generic CER calls
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 766f36ae49d19a11f299fe95f272cc8e72093331
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="bdc9c-102">openGenericCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="bdc9c-102">openGenericCERCall MDA</span></span>
<span data-ttu-id="bdc9c-103">`openGenericCERCall` Yönetilen hata ayıklama Yardımcısı JIT derleme veya yerel görüntü oluşturma zamanı ve en az bir genel kısıtlı yürütme bölge (CER) grafiğe kök yöntemi en genel tür değişkenlerle birlikte işleniyor uyarmak için etkinleştirildi türü değişkenleri olan bir nesne başvurusu türü.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="bdc9c-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="bdc9c-104">Symptoms</span></span>  
 <span data-ttu-id="bdc9c-105">CER kod, bir iş parçacığı iptal edildiğinde veya uygulama etki alanı kaldırıldığında çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="bdc9c-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="bdc9c-106">Cause</span></span>  
 <span data-ttu-id="bdc9c-107">JIT derleme zamanında bir nesne başvurusu türü içeren bir örnek oluşturma yalnızca Sonuç kodu paylaşılan ve her nesne başvurusu türü değişkenleri herhangi bir nesne başvurusu türünün olabilir çünkü temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="bdc9c-108">Bu, bazı çalışma zamanı kaynaklar önceden hazırlanması engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>  
  
 <span data-ttu-id="bdc9c-109">Özellikle, genel tür değişken içeren yöntemlerin gevşek arka planda kaynakları tahsis edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="bdc9c-110">Bunlar, genel bir sözlük girişleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="bdc9c-111">Örneğin, deyim için `List<T> list = new List<T>();` nerede `T` çalışma zamanı aramak ve büyük olasılıkla tam örnek oluşturma zamanında, örneğin, oluşturma genel tür değişken `List<Object>, List<String>`, vb.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`,and so forth.</span></span> <span data-ttu-id="bdc9c-112">Bu, çeşitli nedenlerle çalışan yetersiz bellek gibi geliştirici denetim ötesinde için başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>  
  
 <span data-ttu-id="bdc9c-113">Bu MDA JIT derleme zamanında, tam bir örnek oluşturma olduğunda değil yalnızca etkinleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>  
  
 <span data-ttu-id="bdc9c-114">Bu MDA etkinleştirildiğinde, büyük olasılıkla Belirtiler CERs için hatalı örneklemesi işlevsel olduğundan emin olan.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="bdc9c-115">Aslında, çalışma zamanı CER etkinleştirilecek MDA neden olduğu durumlarda uygulamak çalıştı değil.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="bdc9c-116">Bu nedenle paylaşılan örneklemesi sonra JIT derleme CER, geliştirici kullanıyorsa, genel türler yükleme hataları yazın veya hedeflenen CER bölge içinde iş parçacığı iptalleri yakalanan değil.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="bdc9c-117">Çözüm</span><span class="sxs-lookup"><span data-stu-id="bdc9c-117">Resolution</span></span>  
 <span data-ttu-id="bdc9c-118">Nesne başvurusu türü bir CER içerebilir yöntemleri için genel tür değişkenler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="bdc9c-119">Çalışma zamanı etkisi</span><span class="sxs-lookup"><span data-stu-id="bdc9c-119">Effect on the Runtime</span></span>  
 <span data-ttu-id="bdc9c-120">Bu MDA CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-120">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="bdc9c-121">Çıkış</span><span class="sxs-lookup"><span data-stu-id="bdc9c-121">Output</span></span>  
 <span data-ttu-id="bdc9c-122">Bu MDA çıktısı bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-122">The following is a sample of output from this MDA.</span></span>  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a><span data-ttu-id="bdc9c-123">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="bdc9c-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="bdc9c-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="bdc9c-124">Example</span></span>  
 <span data-ttu-id="bdc9c-125">CER kod yürütülmedi.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-125">The CER code is not executed.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="bdc9c-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-126">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>  
 <xref:System.Runtime.ConstrainedExecution>  
 [<span data-ttu-id="bdc9c-127">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="bdc9c-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
