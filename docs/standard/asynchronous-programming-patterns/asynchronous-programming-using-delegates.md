---
title: Temsilcileri Kullanarak Zaman Uyumsuz Programlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
ms.openlocfilehash: 4e17e6a96a12b705cf455d70add7e12a30f5fa90
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121741"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="da6f5-102">Temsilcileri Kullanarak Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="da6f5-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="da6f5-103">Temsilciler, zaman uyumlu bir yöntemi zaman uyumsuz bir şekilde aramanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="da6f5-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="da6f5-104">Bir temsilciyi zaman uyumlu olarak çağırdığınızda `Invoke` yöntemi hedef yöntemi doğrudan geçerli iş parçacığında çağırır.</span><span class="sxs-lookup"><span data-stu-id="da6f5-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="da6f5-105">`BeginInvoke` yöntemi çağrılırsa, ortak dil çalışma zamanı (CLR) isteği sıralar ve çağrıyı yapana hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="da6f5-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="da6f5-106">Hedef Yöntem, iş parçacığı havuzundan bir iş parçacığında zaman uyumsuz olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="da6f5-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="da6f5-107">İsteği gönderen orijinal iş parçacığı, hedef yöntemiyle paralel olarak yürütmeye devam etmek için ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="da6f5-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="da6f5-108">`BeginInvoke` yöntemine yapılan çağrıda bir geri çağırma yöntemi belirtilmişse, hedef Yöntem sona erdiğinde geri çağırma yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="da6f5-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="da6f5-109">Geri çağırma yönteminde `EndInvoke` yöntemi, dönüş değerini ve herhangi bir giriş/çıkış ya da yalnızca çıkış parametrelerini alır.</span><span class="sxs-lookup"><span data-stu-id="da6f5-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="da6f5-110">`BeginInvoke`çağrılırken hiçbir geri arama yöntemi belirtilmemişse, `EndInvoke` `BeginInvoke`çağıran iş parçacığından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="da6f5-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="da6f5-111">Derleyiciler, Kullanıcı tarafından belirtilen temsilci imzasını kullanarak temsilci sınıflarını `Invoke`, `BeginInvoke`ve `EndInvoke` yöntemlerle yaymalıdır.</span><span class="sxs-lookup"><span data-stu-id="da6f5-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="da6f5-112">`BeginInvoke` ve `EndInvoke` yöntemleri yerel olarak tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da6f5-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="da6f5-113">Bu yöntemler yerel olarak işaretlendiğinden, CLR otomatik olarak uygulamayı sınıf yükleme zamanında sağlar.</span><span class="sxs-lookup"><span data-stu-id="da6f5-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="da6f5-114">Yükleyici, bunların geçersiz kılınmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="da6f5-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="da6f5-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="da6f5-115">In This Section</span></span>  
 [<span data-ttu-id="da6f5-116">Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="da6f5-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="da6f5-117">Sıradan yöntemlere zaman uyumsuz çağrılar yapmak için temsilcilerin kullanımını açıklar ve zaman uyumsuz bir çağrının dönmesi için beklenecek dört yolu gösteren basit kod örnekleri sunar.</span><span class="sxs-lookup"><span data-stu-id="da6f5-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="da6f5-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="da6f5-118">Related Sections</span></span>  
 [<span data-ttu-id="da6f5-119">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="da6f5-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="da6f5-120">.NET Framework zaman uyumsuz programlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="da6f5-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da6f5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da6f5-121">See also</span></span>

- <xref:System.Delegate>
