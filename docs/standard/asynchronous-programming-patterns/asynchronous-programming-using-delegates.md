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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bad5372af1d771dc93a20e61090ef84126f3e1eb
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746867"
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="6ded6-102">Temsilcileri Kullanarak Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="6ded6-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="6ded6-103">Temsilciler, zaman uyumsuz olarak bir zaman uyumlu yöntem çağrısı sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ded6-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="6ded6-104">Zaman uyumlu olarak, bir temsilci çağırdığınızda `Invoke` yöntemi doğrudan geçerli iş parçacığı üzerinde hedef yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="6ded6-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="6ded6-105">Varsa `BeginInvoke` yöntemi çağrıldığında, ortak dil çalışma zamanı (CLR) isteğini sıraya koyar ve hemen çağırana döner.</span><span class="sxs-lookup"><span data-stu-id="6ded6-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="6ded6-106">Hedef yöntemin, iş parçacığı havuzundan bir iş parçacığında zaman uyumsuz olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6ded6-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="6ded6-107">Hedef yöntemin ile paralel yürütmeye devam isteği gönderildi, özgün iş parçacığı, ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="6ded6-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="6ded6-108">Bir geri çağırma yöntemi çağrısında belirtildiğinde `BeginInvoke` yöntemi, geri çağırma yöntemi hedef yöntemin sona erdiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6ded6-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="6ded6-109">Geri çağırma yöntemi `EndInvoke` yöntemi, dönüş değeri ve giriş/çıkış ya da yalnızca çıktı parametreleri alır.</span><span class="sxs-lookup"><span data-stu-id="6ded6-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="6ded6-110">Hiçbir geri çağırma yöntemi çağırırken belirtilmişse `BeginInvoke`, `EndInvoke` çağrılan iş parçacığından çağrılabilir `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="6ded6-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6ded6-111">Derleyiciler, temsilci sınıflarıyla yayma `Invoke`, `BeginInvoke`, ve `EndInvoke` yöntemlerini kullanarak kullanıcı tarafından belirtilen temsilci imzası.</span><span class="sxs-lookup"><span data-stu-id="6ded6-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="6ded6-112">`BeginInvoke` Ve `EndInvoke` yöntemleri düzenlenmiş yerel olarak.</span><span class="sxs-lookup"><span data-stu-id="6ded6-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="6ded6-113">Bu yöntemler, yerel olarak işaretlendikleri CLR sınıfı yükleme zamanında uygulamasını otomatik olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ded6-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="6ded6-114">Yükleyici, bunlar geçersiz kılınmadığını güvence sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ded6-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ded6-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6ded6-115">In This Section</span></span>  
 [<span data-ttu-id="6ded6-116">Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="6ded6-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="6ded6-117">Sıradan bir yöntem zaman uyumsuz çağrı yapmak için temsilciler kullanmayı açıklar ve döndürmek zaman uyumsuz bir çağrı için beklenecek dört yolu gösteren basit kod örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ded6-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6ded6-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6ded6-118">Related Sections</span></span>  
 [<span data-ttu-id="6ded6-119">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="6ded6-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="6ded6-120">.NET Framework ile zaman uyumsuz programlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ded6-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ded6-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ded6-121">See also</span></span>

* <xref:System.Delegate>
