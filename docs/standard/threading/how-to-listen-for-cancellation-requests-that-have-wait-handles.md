---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: bekleyen tutamaçları olan Iptal Isteklerini dinleme'
title: 'Nasıl yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
ms.openlocfilehash: d38e4892457873b3f918582bf154a6a596e9d361
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666803"
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="dbec5-103">Nasıl yapılır: Bekleme Tanıtıcıları İçeren İptal İsteklerini Dinleme</span><span class="sxs-lookup"><span data-stu-id="dbec5-103">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>

<span data-ttu-id="dbec5-104">Bir olayın sinyal vermesini beklediği sırada bir yöntem engellenirse, iptal belirtecinin değerini denetleyebilir ve zamanında yanıt verebilir.</span><span class="sxs-lookup"><span data-stu-id="dbec5-104">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="dbec5-105">İlk örnek, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Birleşik iptal çerçevesini yerel olarak desteklemeyen gibi olaylarla çalışırken bu sorunun nasıl çözüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dbec5-105">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="dbec5-106">İkinci örnekte <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> , Birleşik iptali destekleyen, kullanan daha kolay bir yaklaşım gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dbec5-106">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dbec5-107">"Yalnızca kendi kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satıra kesilir ve "özel durum Kullanıcı kodu tarafından işlenmiyor" yazan bir hata mesajı görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dbec5-107">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="dbec5-108">Bu hata zararsız.</span><span class="sxs-lookup"><span data-stu-id="dbec5-108">This error is benign.</span></span> <span data-ttu-id="dbec5-109">F5 tuşuna basarak bu uygulamadan devam edebilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışına bakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dbec5-109">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="dbec5-110">Visual Studio 'Nun ilk hatada kesilmesini engellemek için **Araçlar, Seçenekler, hata ayıklama, genel** altında "yalnızca kendi kodum" onay kutusunun işaretini kaldırmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="dbec5-110">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbec5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbec5-111">Example</span></span>  

 <span data-ttu-id="dbec5-112">Aşağıdaki örnek, <xref:System.Threading.ManualResetEvent> Birleşik iptali desteklemeyen bekleme tanıtıcılarının engellemesini nasıl engellemenin nasıl yapılacağını göstermek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="dbec5-112">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="dbec5-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="dbec5-113">Example</span></span>  

 <span data-ttu-id="dbec5-114">Aşağıdaki örnek, <xref:System.Threading.ManualResetEventSlim> Birleşik iptalleri destekleyen düzenleme temel temellerini engellemeyi göstermek için bir kullanır.</span><span class="sxs-lookup"><span data-stu-id="dbec5-114">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="dbec5-115">Aynı yaklaşım, ve gibi diğer basit düzenleme temelleri ile de kullanılabilir <xref:System.Threading.Semaphore> `Slim` <xref:System.Threading.CountdownEvent> .</span><span class="sxs-lookup"><span data-stu-id="dbec5-115">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="dbec5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbec5-116">See also</span></span>

- [<span data-ttu-id="dbec5-117">Yönetilen Iş parçacıklarında iptal</span><span class="sxs-lookup"><span data-stu-id="dbec5-117">Cancellation in Managed Threads</span></span>](cancellation-in-managed-threads.md)
