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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121741"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="2d096-102">Temsilcileri Kullanarak Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="2d096-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="2d096-103">Temsilciler, eşzamanlı bir yöntem çağırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d096-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="2d096-104">Bir temsilciyi eşzamanlı olarak çağırdığınızda, `Invoke` yöntem hedef yöntemi doğrudan geçerli iş parçacığına çağırır.</span><span class="sxs-lookup"><span data-stu-id="2d096-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="2d096-105">`BeginInvoke` Yöntem çağrılırsa, ortak dil çalışma süresi (CLR) isteği sıralar ve hemen arayana döner.</span><span class="sxs-lookup"><span data-stu-id="2d096-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="2d096-106">Hedef yöntem iş parçacığı havuzundan bir iş parçacığı üzerinde eşzamanlı olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="2d096-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="2d096-107">İsteği gönderen özgün iş parçacığı, hedef yönteme paralel olarak yürütmeye devam etmek için ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="2d096-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="2d096-108">`BeginInvoke` Yönteme yapılan çağrıda bir geri arama yöntemi belirtilmişse, hedef yöntem sona erdiğinde geri arama yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2d096-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="2d096-109">Geri arama yönteminde `EndInvoke` yöntem, iade değerini ve herhangi bir giriş/çıktı veya yalnızca çıktı parametrelerini elde eder.</span><span class="sxs-lookup"><span data-stu-id="2d096-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="2d096-110">Ararken `BeginInvoke`geri arama yöntemi belirtilmemişse, `EndInvoke` . `BeginInvoke`</span><span class="sxs-lookup"><span data-stu-id="2d096-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2d096-111">Derleyiciler, kullanıcı tarafından `Invoke`belirtilen `BeginInvoke`temsilci `EndInvoke` imzasını kullanarak , ve yöntemleri ile temsilci sınıfları yontmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d096-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="2d096-112">`BeginInvoke` Ve `EndInvoke` yöntemler yerli olarak dekore edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="2d096-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="2d096-113">Bu yöntemler yerel olarak işaretlendirilenden, CLR uygulamayı sınıf yük zamanında otomatik olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d096-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="2d096-114">Yükleyici geçersiz kılınmamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2d096-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d096-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2d096-115">In This Section</span></span>  
 [<span data-ttu-id="2d096-116">Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="2d096-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="2d096-117">Adlı metotlara asynchronous aramalar yapmak için temsilcilerin kullanımını tartışır ve asynchronous çağrısının geri dönmesini beklemenin dört yolunu gösteren basit kod örneği sağlıyor.</span><span class="sxs-lookup"><span data-stu-id="2d096-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2d096-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2d096-118">Related Sections</span></span>  
 [<span data-ttu-id="2d096-119">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="2d096-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="2d096-120">.NET Framework ile eşzamanlı programlamayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="2d096-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d096-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d096-121">See also</span></span>

- <xref:System.Delegate>
