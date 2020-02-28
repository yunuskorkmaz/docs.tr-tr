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
ms.openlocfilehash: bc0d9f481fd212ede55bffde6cc20c3e080629e4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159422"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="e9cb1-102">Güvenlik ve Yarış Durumları</span><span class="sxs-lookup"><span data-stu-id="e9cb1-102">Security and Race Conditions</span></span>
<span data-ttu-id="e9cb1-103">Diğer bir konu alanı, yarış koşullarından yararlanılabilen güvenlik delikleri için olası bir konudur.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="e9cb1-104">Bunun gerçekleşebileceği çeşitli yollar vardır.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="e9cb1-105">İzleyen alt konu, geliştiricinin oluşmaması gereken önemli konuların bazılarını özetler.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="e9cb1-106">Dispose yönteminde yarış koşulları</span><span class="sxs-lookup"><span data-stu-id="e9cb1-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="e9cb1-107">Bir sınıfın **Dispose** yöntemi (daha fazla bilgi için bkz. [çöp toplama](../../../docs/standard/garbage-collection/index.md)) eşitlenmemişse, **Dispose** içindeki temizleme kodu, aşağıdaki örnekte gösterildiği gibi birden çok kez çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e9cb1-108">Bu **Dispose** uygulamasının eşitlenmediği için, ilk bir iş parçacığı tarafından `Cleanup` ve ardından `_myObj` **null**olarak ayarlanmadan önce ikinci bir iş parçacığının çağrılması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="e9cb1-109">Bunun bir güvenlik sorunu olup olmadığı, `Cleanup` kodu çalıştırıldığında ne olacağı hakkında farklılık gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="e9cb1-110">Eşitlenmemiş **Dispose** uygulamalarıyla ilgili önemli bir sorun, dosyalar gibi kaynak tanıtıcılarının kullanımını içerir.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="e9cb1-111">Hatalı bırakma yanlış tanıtıcı kullanılmasına neden olabilir, bu da genellikle güvenlik açıklarına yol açar.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="e9cb1-112">Oluşturuculardaki yarış koşulları</span><span class="sxs-lookup"><span data-stu-id="e9cb1-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="e9cb1-113">Bazı uygulamalarda, sınıf oluşturucularının tamamen çalıştırılmasından önce diğer iş parçacıklarının sınıf üyelerine erişmesi mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="e9cb1-114">Bu durum oluşursa herhangi bir güvenlik sorunu olmadığından emin olmak için tüm sınıf oluşturucularını gözden geçirmeniz ve gerekirse iş parçacıklarını eşitlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="e9cb1-115">Önbelleğe alınmış nesneleri olan yarış koşulları</span><span class="sxs-lookup"><span data-stu-id="e9cb1-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="e9cb1-116">Aşağıdaki örnekte gösterildiği gibi, güvenlik bilgilerini önbelleğe alan veya kod erişimi güvenlik [onayı](../../../docs/framework/misc/using-the-assert-method.md) işlemini kullanan kod, sınıfın diğer kısımları uygun şekilde eşitlenmiyorsa yarış koşullarına açık de olabilir.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e9cb1-117">Aynı nesneye sahip başka bir iş parçacığından çağrılabilecek `DoOtherWork` başka yollar varsa, güvenilmeyen bir arayan bir talebi geçmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="e9cb1-118">Kodunuz güvenlik bilgilerini önbelleğe alıyorsa, bu güvenlik açığı için gözden geçirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="e9cb1-119">Sonlandırıcılar içindeki yarış koşulları</span><span class="sxs-lookup"><span data-stu-id="e9cb1-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="e9cb1-120">Yarış koşulları, bir statik veya yönetilmeyen kaynağa başvuruda bulunan bir nesnede, daha sonra sonlandırıcıda boşaldığı bir nesne içinde de gerçekleşebilir.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="e9cb1-121">Birden çok nesne, bir sınıfın sonlandırıcıda yönetilen bir kaynağı paylaşıyorsa, nesnelerin bu kaynağa tüm erişimi eşitlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9cb1-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9cb1-122">See also</span></span>

- [<span data-ttu-id="e9cb1-123">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e9cb1-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
