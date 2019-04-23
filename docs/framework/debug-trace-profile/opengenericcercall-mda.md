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
ms.openlocfilehash: a9ea2e274bbcd17bcc129de46c753f091501d4c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184294"
---
# <a name="opengenericcercall-mda"></a><span data-ttu-id="2e834-102">openGenericCERCall MDA</span><span class="sxs-lookup"><span data-stu-id="2e834-102">openGenericCERCall MDA</span></span>
<span data-ttu-id="2e834-103">`openGenericCERCall` Yönetilen hata ayıklama Yardımcısı, genel tür değişkenleri kök yöntemi ile kısıtlı yürütme bölge (CER) grafik JIT derleme veya yerel görüntü oluşturma zamanına ve en az bir genel işlenmekte olduğunu uyarmak için etkinleştirildi türü değişkenler olan bir nesne başvuru türü.</span><span class="sxs-lookup"><span data-stu-id="2e834-103">The `openGenericCERCall` managed debugging assistant is activated to warn that a constrained execution region (CER) graph with generic type variables at the root method is being processed at JIT-compilation or native image generation time and at least one of the generic type variables is an object reference type.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="2e834-104">Belirtiler</span><span class="sxs-lookup"><span data-stu-id="2e834-104">Symptoms</span></span>  
 <span data-ttu-id="2e834-105">Bir iş parçacığı iptal edildiğinde veya uygulama etki alanı kaldırıldığında CER kod çalıştırmaz.</span><span class="sxs-lookup"><span data-stu-id="2e834-105">CER code does not run when a thread is aborted or when an application domain is unloaded.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="2e834-106">Sebep</span><span class="sxs-lookup"><span data-stu-id="2e834-106">Cause</span></span>  
 <span data-ttu-id="2e834-107">JIT derleme zamanında örneklemesi içeren bir nesne başvuru türü yalnızca Sonuç kodu paylaşılır ve her nesne başvuru türü değişkenlerin herhangi bir nesne başvuru türü olabilir çünkü temsilcisidir.</span><span class="sxs-lookup"><span data-stu-id="2e834-107">At JIT-compilation time, an instantiation containing an object reference type is only representative because the resultant code is shared, and each of the object reference type variables might be any object reference type.</span></span> <span data-ttu-id="2e834-108">Bu, bazı çalışma zamanı kaynaklar önceden hazırlanması engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="2e834-108">This can prevent the preparation of some run-time resources ahead of time.</span></span>  
  
 <span data-ttu-id="2e834-109">Özellikle, genel tür değişkenleri olan yöntemleri gevşek arka planda kaynakları tahsis edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2e834-109">In particular, methods with generic type variables can lazily allocate resources in the background.</span></span> <span data-ttu-id="2e834-110">Bunlar, genel bir sözlük girişleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2e834-110">These are referred to as generic dictionary entries.</span></span> <span data-ttu-id="2e834-111">Deyim için örneği için `List<T> list = new List<T>();` burada `T` çalışma zamanı aramak ve büyük olasılıkla tam oluşturmada çalışma zamanında, örneğin, oluşturun bir genel tür değişken `List<Object>, List<String>`ve böyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="2e834-111">For instance, for the statement `List<T> list = new List<T>();` where `T` is a generic type variable the runtime must look up and possibly create the exact instantiation at run time, for example, `List<Object>, List<String>`,and so forth.</span></span> <span data-ttu-id="2e834-112">Bu, çeşitli nedenlerle yetersiz bellek çalışıyor gibi geliştiricinin kontrolü için başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e834-112">This can fail for a variety of reasons beyond the developer's control, such as running out of memory.</span></span>  
  
 <span data-ttu-id="2e834-113">Bu MDA, JIT derleme zamanında tam örneklemesi olduğunda değil yalnızca etkinleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2e834-113">This MDA should only be activated at JIT-compilation time, not when there is an exact instantiation.</span></span>  
  
 <span data-ttu-id="2e834-114">Bu MDA etkinleştirildiğinde, büyük olasılıkla Belirtiler CERs hatalı örneklemesi için işlevsel olmayan olan.</span><span class="sxs-lookup"><span data-stu-id="2e834-114">When this MDA is activated, the likely symptoms are that CERs are not functional for the bad instantiations.</span></span> <span data-ttu-id="2e834-115">Aslında, çalışma zamanı etkinleştirilecek MDA neden koşullarda bir CER uygulamak çalıştı değil.</span><span class="sxs-lookup"><span data-stu-id="2e834-115">In fact, the runtime has not attempted to implement a CER under the circumstances that caused the MDA to be activated.</span></span> <span data-ttu-id="2e834-116">Bu nedenle Geliştirici sonra JIT derleme CER paylaşılan bir örneğinin kullanıyorsa, genel türler yükleme hataları yazın ya da iş parçacığı iptalleri hedeflenen CER bölge içinde yakalanır değil.</span><span class="sxs-lookup"><span data-stu-id="2e834-116">So if the developer uses a shared instantiation of the CER, then JIT-compilation errors, generics type loading errors, or thread aborts within the region of the intended CER are not caught.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="2e834-117">Çözüm</span><span class="sxs-lookup"><span data-stu-id="2e834-117">Resolution</span></span>  
 <span data-ttu-id="2e834-118">Nesne başvuru türü bir CER içerebilir yöntemleri için genel tür değişkenler kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="2e834-118">Do not use generic type variables that are of object reference type for methods that may contain a CER.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="2e834-119">Çalışma zamanı üzerindeki etkisi</span><span class="sxs-lookup"><span data-stu-id="2e834-119">Effect on the Runtime</span></span>  
 <span data-ttu-id="2e834-120">Bu mda'nın CLR üzerinde etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2e834-120">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="2e834-121">Çıkış</span><span class="sxs-lookup"><span data-stu-id="2e834-121">Output</span></span>  
 <span data-ttu-id="2e834-122">Bu MDA çıktısı bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2e834-122">The following is a sample of output from this MDA.</span></span>  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## <a name="configuration"></a><span data-ttu-id="2e834-123">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2e834-123">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="2e834-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="2e834-124">Example</span></span>  
 <span data-ttu-id="2e834-125">CER kod yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="2e834-125">The CER code is not executed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2e834-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e834-126">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>
- <xref:System.Runtime.ConstrainedExecution>
- [<span data-ttu-id="2e834-127">Yönetilen Hata Ayıklama Yardımcıları ile Hataları Tanılama</span><span class="sxs-lookup"><span data-stu-id="2e834-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
