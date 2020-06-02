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
ms.openlocfilehash: e44b10b88bef61edcf3f547f56b4020740530e26
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279549"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="829e5-102">Nasıl Yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme</span><span class="sxs-lookup"><span data-stu-id="829e5-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="829e5-103">Bir olayın sinyal vermesini beklediği sırada bir yöntem engellenirse, iptal belirtecinin değerini denetleyebilir ve zamanında yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="829e5-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="829e5-104">İlk örnek, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Birleşik iptal çerçevesini yerel olarak desteklemeyen gibi olaylarla çalışırken bu sorunun nasıl çözüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="829e5-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="829e5-105">İkinci örnekte <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> , Birleşik iptali destekleyen, kullanan daha kolay bir yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="829e5-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="829e5-106">"Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="829e5-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="829e5-107">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="829e5-107">This error is benign.</span></span> <span data-ttu-id="829e5-108">F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="829e5-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="829e5-109">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel**altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="829e5-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="829e5-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="829e5-110">Example</span></span>  
 <span data-ttu-id="829e5-111">Aşağıdaki örnek, <xref:System.Threading.ManualResetEvent> Birleşik iptali desteklemeyen bekleme tanıtıcılarının engellemesini nasıl engellemenin nasıl yapılacağını göstermek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="829e5-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="829e5-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="829e5-112">Example</span></span>  
 <span data-ttu-id="829e5-113">Aşağıdaki örnek, <xref:System.Threading.ManualResetEventSlim> Birleşik iptalleri destekleyen düzenleme temel temellerini engellemeyi göstermek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="829e5-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="829e5-114">Aynı yaklaşım, ve gibi diğer basit düzenleme temelleri ile de kullanılabilir <xref:System.Threading.Semaphore> `Slim` <xref:System.Threading.CountdownEvent> .</span><span class="sxs-lookup"><span data-stu-id="829e5-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="829e5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="829e5-115">See also</span></span>

- [<span data-ttu-id="829e5-116">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="829e5-116">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
