---
title: Güvenlik ve Yarış Durumları
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
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
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186786"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="a39e5-102">Güvenlik ve Yarış Durumları</span><span class="sxs-lookup"><span data-stu-id="a39e5-102">Security and Race Conditions</span></span>
<span data-ttu-id="a39e5-103">Endişe edilen bir diğer konu da ırk koşullarının yararlanmış güvenlik açıkları potansiyeli.</span><span class="sxs-lookup"><span data-stu-id="a39e5-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="a39e5-104">Bunun olabileceği çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="a39e5-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="a39e5-105">İzleyen alt konular, geliştiricinin kaçınması gereken bazı önemli tuzakları sıralar.</span><span class="sxs-lookup"><span data-stu-id="a39e5-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="a39e5-106">Elden Çıkarma Yönteminde Yarış Koşulları</span><span class="sxs-lookup"><span data-stu-id="a39e5-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="a39e5-107">Bir sınıfın **Elden Çıkarma** yöntemi (daha fazla bilgi için bkz. [Çöp Toplama)](../../../docs/standard/garbage-collection/index.md)eşitlenmemişse, Aşağıdaki örnekte gösterildiği **gibi, Elden Çıkarma** içindeki temizleme kodunun birden çok kez çalıştırılması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a39e5-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a39e5-108">Bu **Elden Çıkarma** uygulaması eşitlenmediği için, `Cleanup` önce bir iş parçacığı tarafından çağrılması ve daha sonra ikinci bir iş parçacığının `_myObj` **null**olarak ayarlanmaması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a39e5-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="a39e5-109">Bunun bir güvenlik sorunu olup `Cleanup` olmadığı, kod çalıştığında ne olduğuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a39e5-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="a39e5-110">Eşitlenmemiş **Elden Çıkarma** uygulamalarıyla ilgili önemli bir sorun, dosyalar gibi kaynak iştamaçlarının kullanılmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a39e5-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="a39e5-111">Yanlış imha, yanlış tanıtıcının kullanılmasına neden olabilir ve bu da genellikle güvenlik açıklarına yol açar.</span><span class="sxs-lookup"><span data-stu-id="a39e5-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="a39e5-112">İnşaatçılarda Yarış Koşulları</span><span class="sxs-lookup"><span data-stu-id="a39e5-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="a39e5-113">Bazı uygulamalarda, sınıf oluşturucuları tamamen çalışmadan önce diğer iş parçacıklarının sınıf üyelerine erişebilmeleri mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="a39e5-114">Bu olması durumunda güvenlik sorunları olmadığından emin olmak için tüm sınıf oluşturucuları gözden geçirmeniz veya gerekirse iş parçacığı eşitleme niz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="a39e5-115">Önbelleğe Alınmış Nesnelerle Yarış Koşulları</span><span class="sxs-lookup"><span data-stu-id="a39e5-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="a39e5-116">Güvenlik bilgilerini önbelleğe alan veya kod erişim güvenliğini kullanan [kod,](../../../docs/framework/misc/using-the-assert-method.md) aşağıdaki örnekte gösterildiği gibi sınıfın diğer bölümleri uygun şekilde eşitlenmezse, ırk koşullarına karşı savunmasız da olabilir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="a39e5-117">Aynı nesneye `DoOtherWork` sahip başka bir iş parçacığından çağrılabilen başka yollar varsa, güvenilmeyen bir arayan talebi niçin geçebilir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="a39e5-118">Kodunuz güvenlik bilgilerini önbelleğe alırsa, bu güvenlik açığı için bu bilgileri gözden geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a39e5-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="a39e5-119">Finalize'lerde Yarış Koşulları</span><span class="sxs-lookup"><span data-stu-id="a39e5-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="a39e5-120">Yarış koşulları, daha sonra sonlandırıcısında serbest kaldığı statik veya yönetilmeyen bir kaynağa başvuran bir nesnede de oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="a39e5-121">Birden çok nesne, sınıfın sonlandırıcısında manipüle edilen bir kaynağı paylaşıyorsa, nesnelerin bu kaynağa tüm erişimi eşitlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="a39e5-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39e5-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a39e5-122">See also</span></span>

- [<span data-ttu-id="a39e5-123">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="a39e5-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
