---
title: 'Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1c8bfea5fc55bafbaa30d3b74edf60b674ef75c
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46519480"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="b2cca-102">Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme</span><span class="sxs-lookup"><span data-stu-id="b2cca-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="b2cca-103">Bir olay için sinyal bekliyor ancak bir yöntem engellenirse bu iptal belirteci değerini kontrol edin ve zamanında yanıt.</span><span class="sxs-lookup"><span data-stu-id="b2cca-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="b2cca-104">İlk örnek gibi olaylar ile çalışırken, bu sorunu çözmek gösterilmektedir <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> yerel olarak desteklemeyen birleşik iptalini çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="b2cca-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="b2cca-105">İkinci örnek kullanan daha kolay bir yaklaşımı gösterir <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, iptal birleşik hangi desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="b2cca-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b2cca-106">"Yalnızca kendi kodum" etkin olduğunda, bazı durumlarda Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler</span><span class="sxs-lookup"><span data-stu-id="b2cca-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="b2cca-107">Bu hata zararsızdır.</span><span class="sxs-lookup"><span data-stu-id="b2cca-107">This error is benign.</span></span> <span data-ttu-id="b2cca-108">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın.</span><span class="sxs-lookup"><span data-stu-id="b2cca-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="b2cca-109">Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="b2cca-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2cca-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2cca-110">Example</span></span>  
 <span data-ttu-id="b2cca-111">Aşağıdaki örnekte bir <xref:System.Threading.ManualResetEvent> birleşik iptal desteklemeyen bekleme tanıtıcıları engelini kaldırma işlemini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="b2cca-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="b2cca-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2cca-112">Example</span></span>  
 <span data-ttu-id="b2cca-113">Aşağıdaki örnekte bir <xref:System.Threading.ManualResetEventSlim> koordinasyon engelini kaldırma işlemini göstermek için destek temelleri iptal birleşik.</span><span class="sxs-lookup"><span data-stu-id="b2cca-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="b2cca-114">Diğer hafif koordinasyon temelleri ile aynı yaklaşımı gibi kullanılabilir <xref:System.Threading.Semaphore> `Slim` ve <xref:System.Threading.CountdownEvent>.</span><span class="sxs-lookup"><span data-stu-id="b2cca-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="b2cca-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2cca-115">See also</span></span>

- [<span data-ttu-id="b2cca-116">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="b2cca-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
