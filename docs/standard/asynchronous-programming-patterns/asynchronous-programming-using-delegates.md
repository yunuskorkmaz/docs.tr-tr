---
description: 'Daha fazla bilgi edinin: temsilcileri kullanarak zaman uyumsuz programlama'
title: Temsilcileri Kullanarak Zaman Uyumsuz Programlama
ms.date: 03/30/2017
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
ms.openlocfilehash: 5315324fa79ce4658c255dbc09cd71a09afc614c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703113"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="22a44-103">Temsilcileri Kullanarak Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="22a44-103">Asynchronous Programming Using Delegates</span></span>

<span data-ttu-id="22a44-104">Temsilciler, zaman uyumlu bir yöntemi zaman uyumsuz bir şekilde aramanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="22a44-104">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="22a44-105">Bir temsilciyi zaman uyumlu olarak çağırdığınızda, `Invoke` yöntemi hedef yöntemi doğrudan geçerli iş parçacığında çağırır.</span><span class="sxs-lookup"><span data-stu-id="22a44-105">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="22a44-106">`BeginInvoke`Yöntemi çağrılırsa, ortak dil çalışma zamanı (CLR) isteği sıraya alır ve hemen çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="22a44-106">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="22a44-107">Hedef Yöntem, iş parçacığı havuzundan bir iş parçacığında zaman uyumsuz olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="22a44-107">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="22a44-108">İsteği gönderen orijinal iş parçacığı, hedef yöntemiyle paralel olarak yürütmeye devam etmek için ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="22a44-108">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="22a44-109">Yöntemine yapılan çağrıda bir geri çağırma yöntemi belirtilmişse `BeginInvoke` , hedef Yöntem sona erdiğinde geri çağırma yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="22a44-109">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="22a44-110">Geri çağırma yönteminde, `EndInvoke` yöntemi dönüş değerini ve herhangi bir giriş/çıkış veya yalnızca çıkış parametrelerini alır.</span><span class="sxs-lookup"><span data-stu-id="22a44-110">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="22a44-111">Çağrılırken hiçbir geri arama yöntemi belirtilmemişse, çağıran `BeginInvoke` `EndInvoke` iş parçacığından çağrılabilir `BeginInvoke` .</span><span class="sxs-lookup"><span data-stu-id="22a44-111">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="22a44-112">Derleyiciler `Invoke` , `BeginInvoke` `EndInvoke` Kullanıcı tarafından belirtilen temsilci imzasını kullanarak,, ve yöntemleriyle temsilci sınıfları göstermelidir.</span><span class="sxs-lookup"><span data-stu-id="22a44-112">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="22a44-113">`BeginInvoke`Ve `EndInvoke` yöntemleri yerel olarak tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="22a44-113">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="22a44-114">Bu yöntemler yerel olarak işaretlendiğinden, CLR otomatik olarak uygulamayı sınıf yükleme zamanında sağlar.</span><span class="sxs-lookup"><span data-stu-id="22a44-114">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="22a44-115">Yükleyici, bunların geçersiz kılınmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="22a44-115">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22a44-116">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="22a44-116">In This Section</span></span>  

 [<span data-ttu-id="22a44-117">Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="22a44-117">Calling Synchronous Methods Asynchronously</span></span>](calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="22a44-118">Sıradan yöntemlere zaman uyumsuz çağrılar yapmak için temsilcilerin kullanımını açıklar ve zaman uyumsuz bir çağrının dönmesi için beklenecek dört yolu gösteren basit kod örnekleri sunar.</span><span class="sxs-lookup"><span data-stu-id="22a44-118">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="22a44-119">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="22a44-119">Related Sections</span></span>  

 [<span data-ttu-id="22a44-120">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="22a44-120">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="22a44-121">.NET 'te zaman uyumsuz programlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="22a44-121">Describes asynchronous programming in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a44-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22a44-122">See also</span></span>

- <xref:System.Delegate>
