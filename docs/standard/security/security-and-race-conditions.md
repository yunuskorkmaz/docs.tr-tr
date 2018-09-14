---
title: Güvenlik ve Yarış Durumları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57ceaedc7c38ae70a0db5a7fd584a765a7474aff
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45593172"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="47941-102">Güvenlik ve Yarış Durumları</span><span class="sxs-lookup"><span data-stu-id="47941-102">Security and Race Conditions</span></span>
<span data-ttu-id="47941-103">Başka bir sorun olası güvenlik açıkları yarış koşulları tarafından kötüye alanıdır.</span><span class="sxs-lookup"><span data-stu-id="47941-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="47941-104">Bu gerçekleşebilir birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="47941-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="47941-105">Aşağıdaki alt konuları Geliştirici kaçınmalısınız ana düşebileceğiniz tuzakları bazıları özetler.</span><span class="sxs-lookup"><span data-stu-id="47941-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="47941-106">Dispose yöntemi yarış koşulları</span><span class="sxs-lookup"><span data-stu-id="47941-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="47941-107">Bir sınıf, ın **Dispose** yöntemi (daha fazla bilgi için bkz. [çöp toplama](../../../docs/standard/garbage-collection/index.md)) olan eşitlenmemiş, mümkündür içinde temizleme kodu **Dispose** çalıştırılabilir birden fazla Aşağıdaki örnekte gösterildiği gibi kez.</span><span class="sxs-lookup"><span data-stu-id="47941-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()   
{  
    if (myObj != null)   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="47941-108">Çünkü bu **Dispose** uygulama eşitlenmemiş, mümkündür `Cleanup` ilk iş parçacığı ve önce ikinci bir iş parçacığı tarafından çağrılacak `_myObj` ayarlanır **null**.</span><span class="sxs-lookup"><span data-stu-id="47941-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="47941-109">Bu bir güvenlik sorunu olup olmadığını bağlıdır ne olur olduğunda `Cleanup` kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="47941-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="47941-110">Önemli bir sorun ile eşitlenmemiş **Dispose** uygulamaları dosyalar gibi kaynak tanıtıcıları kullanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="47941-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="47941-111">Hatalı elden çıkarma, genellikle güvenlik açıklarını müşteri adayları kullanılmak üzere yanlış tanıtıcı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="47941-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="47941-112">Oluşturucularda yarış durumları</span><span class="sxs-lookup"><span data-stu-id="47941-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="47941-113">Bazı uygulamalarda, sınıf oluşturucuları tamamen çalıştırmadan önce sınıf üyelerinin erişmek diğer iş parçacıkları için mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="47941-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="47941-114">Bu durum veya gerekirse iş parçacığı eşitleme, hiçbir güvenlik sorunu olduğundan emin olmak için tüm sınıf oluşturucuları gözden geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47941-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="47941-115">Önbelleğe alınan nesneleri ile yarış durumları</span><span class="sxs-lookup"><span data-stu-id="47941-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="47941-116">Güvenlik bilgileri önbelleğe alır veya kod erişimi güvenliği kullanan kod [Assert](../../../docs/framework/misc/using-the-assert-method.md) işlem de olabilir yarış durumlarını savunmasız sınıfı diğer bölümlerini uygun şekilde eşitlenmemişse, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="47941-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()   
{  
    if (SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()   
{  
    if (fCallersOK)   
    {  
        DoSomethingTrusted();  
    }  
    else   
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 <span data-ttu-id="47941-117">Diğer yollara varsa `DoOtherWork` aynı nesneye sahip başka bir iş parçacığından çağrılabilir, güvenilmeyen bir çağıranın isteğe bağlı Koçan.</span><span class="sxs-lookup"><span data-stu-id="47941-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="47941-118">Kodunuzu güvenlik bilgilerini önbelleğe alıyorsa, bu güvenlik açığı için incelemeyi unutmayın.</span><span class="sxs-lookup"><span data-stu-id="47941-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="47941-119">Sonlandırıcılar yarış koşulları</span><span class="sxs-lookup"><span data-stu-id="47941-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="47941-120">Ardından nesnenin Sonlandırıcısı serbest bırakan bir statik veya yönetilmeyen kaynağa başvuran bir nesnedeki yarış durumları da meydana gelebilir.</span><span class="sxs-lookup"><span data-stu-id="47941-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="47941-121">Nesneleri, birden çok nesne bir sınıfın Sonlandırıcı içinde yönetilen bir kaynak paylaşıyorsanız, tüm bu kaynağa erişimi eşitlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="47941-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47941-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47941-122">See also</span></span>

- [<span data-ttu-id="47941-123">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="47941-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
