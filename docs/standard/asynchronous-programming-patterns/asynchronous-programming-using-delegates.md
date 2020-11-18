---
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
ms.openlocfilehash: da468d3b16ee504317c7de2e216a9be2073d1cf3
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830512"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="cdc6f-102">Temsilcileri Kullanarak Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="cdc6f-102">Asynchronous Programming Using Delegates</span></span>

<span data-ttu-id="cdc6f-103">Temsilciler, zaman uyumlu bir yöntemi zaman uyumsuz bir şekilde aramanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="cdc6f-104">Bir temsilciyi zaman uyumlu olarak çağırdığınızda, `Invoke` yöntemi hedef yöntemi doğrudan geçerli iş parçacığında çağırır.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="cdc6f-105">`BeginInvoke`Yöntemi çağrılırsa, ortak dil çalışma zamanı (CLR) isteği sıraya alır ve hemen çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="cdc6f-106">Hedef Yöntem, iş parçacığı havuzundan bir iş parçacığında zaman uyumsuz olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="cdc6f-107">İsteği gönderen orijinal iş parçacığı, hedef yöntemiyle paralel olarak yürütmeye devam etmek için ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="cdc6f-108">Yöntemine yapılan çağrıda bir geri çağırma yöntemi belirtilmişse `BeginInvoke` , hedef Yöntem sona erdiğinde geri çağırma yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="cdc6f-109">Geri çağırma yönteminde, `EndInvoke` yöntemi dönüş değerini ve herhangi bir giriş/çıkış veya yalnızca çıkış parametrelerini alır.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="cdc6f-110">Çağrılırken hiçbir geri arama yöntemi belirtilmemişse, çağıran `BeginInvoke` `EndInvoke` iş parçacığından çağrılabilir `BeginInvoke` .</span><span class="sxs-lookup"><span data-stu-id="cdc6f-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cdc6f-111">Derleyiciler `Invoke` , `BeginInvoke` `EndInvoke` Kullanıcı tarafından belirtilen temsilci imzasını kullanarak,, ve yöntemleriyle temsilci sınıfları göstermelidir.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="cdc6f-112">`BeginInvoke`Ve `EndInvoke` yöntemleri yerel olarak tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="cdc6f-113">Bu yöntemler yerel olarak işaretlendiğinden, CLR otomatik olarak uygulamayı sınıf yükleme zamanında sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="cdc6f-114">Yükleyici, bunların geçersiz kılınmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cdc6f-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cdc6f-115">In This Section</span></span>  
 [<span data-ttu-id="cdc6f-116">Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="cdc6f-116">Calling Synchronous Methods Asynchronously</span></span>](calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="cdc6f-117">Sıradan yöntemlere zaman uyumsuz çağrılar yapmak için temsilcilerin kullanımını açıklar ve zaman uyumsuz bir çağrının dönmesi için beklenecek dört yolu gösteren basit kod örnekleri sunar.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cdc6f-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="cdc6f-118">Related Sections</span></span>  
 [<span data-ttu-id="cdc6f-119">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="cdc6f-119">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="cdc6f-120">.NET 'te zaman uyumsuz programlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-120">Describes asynchronous programming in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc6f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdc6f-121">See also</span></span>

- <xref:System.Delegate>
