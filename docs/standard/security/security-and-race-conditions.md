---
title: "Güvenlik ve Yarış Durumları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 73664df9c072189f11d451da46bc3019c8593ec9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="416ee-102">Güvenlik ve Yarış Durumları</span><span class="sxs-lookup"><span data-stu-id="416ee-102">Security and Race Conditions</span></span>
<span data-ttu-id="416ee-103">Başka bir sorun olası güvenlik açıklarını yarış durumları tarafından yararlanan alanıdır.</span><span class="sxs-lookup"><span data-stu-id="416ee-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="416ee-104">Bu durum oluşabilir birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="416ee-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="416ee-105">İzleyin konuları Geliştirici kaçınmalısınız ana Tuzaklar bazıları verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="416ee-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="416ee-106">Dispose yöntemi yarış durumları</span><span class="sxs-lookup"><span data-stu-id="416ee-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="416ee-107">Bir sınıf, kullanıcının **Dispose** yöntemi (daha fazla bilgi için bkz: [çöp toplama](../../../docs/standard/garbage-collection/index.md)) olan eşitlenmiş değil, mümkündür içinde kodu Temizleme **Dispose** çalıştırılabilir birden fazla Aşağıdaki örnekte gösterildiği gibi bir kez.</span><span class="sxs-lookup"><span data-stu-id="416ee-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="416ee-108">Çünkü bu **Dispose** uygulama eşitlenmemiş, mümkündür `Cleanup` önce bir iş parçacığı ve ardından ikinci bir iş parçacığı önce çağrılacak `_myObj` ayarlanır **null**.</span><span class="sxs-lookup"><span data-stu-id="416ee-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="416ee-109">Bu bir güvenlik sorunu olup olmadığını bağlıdır ne olacağını zaman `Cleanup` kodu çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="416ee-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="416ee-110">Eşitlenmemiş bir önemli sorun **Dispose** uygulamaları dosyaları gibi kaynak tanıtıcıları kullanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="416ee-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="416ee-111">Hatalı elden, genellikle güvenlik açıkları için müşteri adayları kullanılmak üzere yanlış tanıtıcı neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="416ee-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="416ee-112">Yapıcılardaki yarış durumları</span><span class="sxs-lookup"><span data-stu-id="416ee-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="416ee-113">Bazı uygulamalarda, kendi sınıf oluşturucular tamamen çalıştırmadan önce sınıf üyeleri erişmek başka bir iş parçacığı için mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="416ee-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="416ee-114">Bu ortaya veya gerekiyorsa, iş parçacığı eşitleme hiçbir güvenlik sorunları olduğundan emin olmak için tüm sınıf oluşturucular gözden geçirmelidir.</span><span class="sxs-lookup"><span data-stu-id="416ee-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="416ee-115">Önbelleğe alınan nesnelerle yarış durumları</span><span class="sxs-lookup"><span data-stu-id="416ee-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="416ee-116">Güvenlik bilgileri önbelleğe alır veya kod erişim güvenliği kullanan kodu [Assert](../../../docs/framework/misc/using-the-assert-method.md) işlemi de olabilir yarış durumları savunmasız sınıfı diğer bölümleri uygun şekilde eşitlenmemişse, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="416ee-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
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
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
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
  
 <span data-ttu-id="416ee-117">Diğer yolları varsa `DoOtherWork` aynı nesneye sahip başka bir iş parçacığından çağrılabilir, güvenilmeyen bir çağıran bir isteğe bağlı irsaliyesi.</span><span class="sxs-lookup"><span data-stu-id="416ee-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="416ee-118">Kodunuzu güvenlik bilgileri önbelleğe alır, bu güvenlik açığı gözden emin olun.</span><span class="sxs-lookup"><span data-stu-id="416ee-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="416ee-119">Sonlandırıcılar yarış durumları</span><span class="sxs-lookup"><span data-stu-id="416ee-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="416ee-120">Yarış durumları sonra onun sonlandırıcıyı boşaltır statik veya yönetilmeyen bir kaynağa başvuran bir nesnedeki da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="416ee-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="416ee-121">Birden çok nesne sınıf sonlandırıcıyı yönetilebilir bir kaynak paylaşıyorsanız, nesneleri bu kaynağa hiçbir erişim eşitlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="416ee-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="416ee-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="416ee-122">See Also</span></span>  
 [<span data-ttu-id="416ee-123">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="416ee-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
