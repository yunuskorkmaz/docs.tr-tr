---
title: 'Nasıl Yapılır: Birden Çok İptal İsteğini Dinleme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afa22ed1fe1986712493c2aaa844d7f2c6ffd5bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583136"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="639f8-102">Nasıl Yapılır: Birden Çok İptal İsteğini Dinleme</span><span class="sxs-lookup"><span data-stu-id="639f8-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="639f8-103">Bu örnek, ya da belirteci isterse bir işlem iptal edebilirsiniz iki iptal belirteçlerini aynı anda dinlenecek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="639f8-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="639f8-104">"Sadece kendi kodumu" etkinleştirildiğinde, Visual Studio bazı durumlarda, özel durum oluşturur satır başı ve "özel durum kullanıcı kodu tarafından işlenmiyor." diyen bir hata iletisi görüntülenir</span><span class="sxs-lookup"><span data-stu-id="639f8-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="639f8-105">Bu hata zararsız kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="639f8-105">This error is benign.</span></span> <span data-ttu-id="639f8-106">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterildiği özel durum işleme davranışı bakın.</span><span class="sxs-lookup"><span data-stu-id="639f8-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="639f8-107">Visual Studio ilk hatada kesilmesini önlemek için yalnızca altında "Sadece kendi kodumu" onay kutusunun işaretini **Araçlar, seçenekleri, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="639f8-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="639f8-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="639f8-108">Example</span></span>  
 <span data-ttu-id="639f8-109">Aşağıdaki örnekte, <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> yöntemi iki belirteci bir belirteç katılmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="639f8-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="639f8-110">Bu yalnızca bir iptal belirteci bağımsız değişken olarak ele yöntemleri geçirilmesi için belirteci sağlar.</span><span class="sxs-lookup"><span data-stu-id="639f8-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="639f8-111">Örnek bir yöntem gelen dışında sınıfı ve sınıf içinde oluşturulan bir belirteç geçirilen hem bir belirteç uymanız gerekir yaygın bir senaryo gösterir.</span><span class="sxs-lookup"><span data-stu-id="639f8-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="639f8-112">Ne zaman bağlantılı belirteci oluşturur bir <xref:System.OperationCanceledException>, özel durumu geçirilen belirteç bağlantılı, öncül belirteçlerin ya belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="639f8-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="639f8-113">Hangi belirteçlerin iptal edildi belirlemek için doğrudan öncül belirteçleri durumunu kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="639f8-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="639f8-114">Bu örnekte, <xref:System.AggregateException> hiçbir zaman oluşturulması, ancak çünkü burada yakaladığı gerçek dünya senaryolarında yanı sıra diğer tüm özel durumlar <xref:System.OperationCanceledException> görev temsilciden oluşturulan içinde kaydırılan bir <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="639f8-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="639f8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="639f8-115">See Also</span></span>  
 [<span data-ttu-id="639f8-116">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="639f8-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
