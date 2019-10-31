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
ms.openlocfilehash: 43ca52359a48d3ac5a27933fcc8ce56c07159cac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137986"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="0a3fc-102">Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme</span><span class="sxs-lookup"><span data-stu-id="0a3fc-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="0a3fc-103">Bir olayın sinyal vermesini beklediği sırada bir yöntem engellenirse, iptal belirtecinin değerini denetleyebilir ve zamanında yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="0a3fc-104">İlk örnek, Birleşik iptal çerçevesini yerel olarak desteklemeyen <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> gibi olaylarla çalışırken bu sorunun nasıl çözüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="0a3fc-105">İkinci örnekte, Birleşik iptali destekleyen <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>kullanan daha kolay bir yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a3fc-106">"Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="0a3fc-107">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-107">This error is benign.</span></span> <span data-ttu-id="0a3fc-108">F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="0a3fc-109">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a3fc-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a3fc-110">Example</span></span>  
 <span data-ttu-id="0a3fc-111">Aşağıdaki örnek, Birleşik iptali desteklemeyen bekleme tanıtıcılarının engellemesini kaldırmayı göstermek için bir <xref:System.Threading.ManualResetEvent> kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="0a3fc-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="0a3fc-112">Example</span></span>  
 <span data-ttu-id="0a3fc-113">Aşağıdaki örnek, Birleşik iptalleri destekleyen düzenleme temel temellerini engellemeyi göstermek için bir <xref:System.Threading.ManualResetEventSlim> kullanır.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="0a3fc-114">Aynı yaklaşım, <xref:System.Threading.Semaphore>`Slim` ve <xref:System.Threading.CountdownEvent>gibi diğer basit koordinasyon temelleri ile de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="0a3fc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a3fc-115">See also</span></span>

- [<span data-ttu-id="0a3fc-116">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="0a3fc-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
