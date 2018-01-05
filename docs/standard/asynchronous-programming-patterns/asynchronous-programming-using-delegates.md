---
title: Temsilcileri Kullanarak Zaman Uyumsuz Programlama
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e84c004c8efc58c6d6ad55674470bec13fc0bab8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="asynchronous-programming-using-delegates"></a><span data-ttu-id="2740b-102">Temsilcileri Kullanarak Zaman Uyumsuz Programlama</span><span class="sxs-lookup"><span data-stu-id="2740b-102">Asynchronous Programming Using Delegates</span></span>
<span data-ttu-id="2740b-103">Temsilciler bir zaman uyumsuz olarak zaman uyumlu bir yöntemi çağırmak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="2740b-103">Delegates enable you to call a synchronous method in an asynchronous manner.</span></span> <span data-ttu-id="2740b-104">Zaman uyumlu olarak, bir temsilciyi çağırdığınızda `Invoke` yöntemi doğrudan geçerli iş parçacığı üzerinde hedef yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="2740b-104">When you call a delegate synchronously, the `Invoke` method calls the target method directly on the current thread.</span></span> <span data-ttu-id="2740b-105">Varsa `BeginInvoke` yöntemi çağrıldığında, ortak dil çalışma zamanı (CLR) isteğini sıraya koyar ve hemen çağırana döndürür.</span><span class="sxs-lookup"><span data-stu-id="2740b-105">If the `BeginInvoke` method is called, the common language runtime (CLR) queues the request and returns immediately to the caller.</span></span> <span data-ttu-id="2740b-106">Hedef yöntemin iş parçacığı havuzundaki iş parçacığı üzerinde zaman uyumsuz olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2740b-106">The target method is called asynchronously on a thread from the thread pool.</span></span> <span data-ttu-id="2740b-107">İstek gönderildi, orijinal iş parçacığı, hedef yöntemin ile Paralel yürütme devam etmek ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="2740b-107">The original thread, which submitted the request, is free to continue executing in parallel with the target method.</span></span> <span data-ttu-id="2740b-108">Bir geri çağırma yöntemi çağrısında belirtildiğinde `BeginInvoke` yöntemi, geri çağırma yöntemi hedef yöntemin bittikten sonra çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2740b-108">If a callback method has been specified in the call to the `BeginInvoke` method, the callback method is called when the target method ends.</span></span> <span data-ttu-id="2740b-109">Geri çağırma yöntemi `EndInvoke` yöntemi, dönüş değeri ve giriş/çıkış ya da yalnızca çıktı parametreleri alır.</span><span class="sxs-lookup"><span data-stu-id="2740b-109">In the callback method, the `EndInvoke` method obtains the return value and any input/output or output-only parameters.</span></span> <span data-ttu-id="2740b-110">Geri çağırma yöntemi çağrılırken belirtilmişse `BeginInvoke`, `EndInvoke` çağıran iş parçacığının çağrılabilir `BeginInvoke`.</span><span class="sxs-lookup"><span data-stu-id="2740b-110">If no callback method is specified when calling `BeginInvoke`, `EndInvoke` can be called from the thread that called `BeginInvoke`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2740b-111">Derleyicileri temsilci sınıflarıyla yayma `Invoke`, `BeginInvoke`, ve `EndInvoke` yöntemlerini kullanarak kullanıcı tarafından belirtilen temsilci imzası.</span><span class="sxs-lookup"><span data-stu-id="2740b-111">Compilers should emit delegate classes with `Invoke`, `BeginInvoke`, and `EndInvoke` methods using the delegate signature specified by the user.</span></span> <span data-ttu-id="2740b-112">`BeginInvoke` Ve `EndInvoke` yöntemleri donatılmış olarak yerel.</span><span class="sxs-lookup"><span data-stu-id="2740b-112">The `BeginInvoke` and `EndInvoke` methods should be decorated as native.</span></span> <span data-ttu-id="2740b-113">Bu yöntemler yerel olarak işaretlenmiş olduğundan, CLR uygulamasını sınıf yükleme zamanında otomatik olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="2740b-113">Because these methods are marked as native, the CLR automatically provides the implementation at class load time.</span></span> <span data-ttu-id="2740b-114">Bunlar değil geçersiz yükleyici sağlar.</span><span class="sxs-lookup"><span data-stu-id="2740b-114">The loader ensures that they are not overridden.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2740b-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2740b-115">In This Section</span></span>  
 [<span data-ttu-id="2740b-116">Zaman Uyumlu Metotları Zaman Uyumsuz Olarak Çağırma</span><span class="sxs-lookup"><span data-stu-id="2740b-116">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="2740b-117">Sıradan yöntemleri zaman uyumsuz çağrı yapmak için temsilciler kullanmayı açıklar ve bir zaman uyumsuz çağrı döndürmek beklenecek dört yolu Göster basit kod örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="2740b-117">Discusses the use of delegates to make asynchronous calls to ordinary methods, and provides simple code examples that show the four ways to wait for an asynchronous call to return.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2740b-118">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2740b-118">Related Sections</span></span>  
 [<span data-ttu-id="2740b-119">Olay Tabanlı Zaman Uyumsuz Desen (EAP)</span><span class="sxs-lookup"><span data-stu-id="2740b-119">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 <span data-ttu-id="2740b-120">.NET Framework ile zaman uyumsuz programlama açıklar.</span><span class="sxs-lookup"><span data-stu-id="2740b-120">Describes asynchronous programming with the .NET Framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2740b-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2740b-121">See Also</span></span>  
 <xref:System.Delegate>
