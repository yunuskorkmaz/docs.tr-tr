---
title: 'Nasıl yapılır: Birden Çok İptal İsteğini Dinleme'
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
ms.openlocfilehash: 17874b8b9733ea18d4877e2c79810fcd6247db0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61926207"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="7bcd3-102">Nasıl yapılır: Birden Çok İptal İsteğini Dinleme</span><span class="sxs-lookup"><span data-stu-id="7bcd3-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="7bcd3-103">Bu örnek, bir işlem ya da belirteç istediği zaman iptal edebilirsiniz iki iptal belirteçleri için aynı anda dinlenecek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7bcd3-104">"Yalnızca kendi kodum" etkin olduğunda, bazı durumlarda Visual Studio özel durum oluşturan satırda bölme ve "özel durum kullanıcı kodu tarafından işlenmemiş." diyen bir hata iletisini görüntüler</span><span class="sxs-lookup"><span data-stu-id="7bcd3-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="7bcd3-105">Bu hata zararsızdır.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-105">This error is benign.</span></span> <span data-ttu-id="7bcd3-106">Buradan devam etmek için F5 tuşuna basın ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını bakın.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="7bcd3-107">Visual Studio'nun çalışmasının ilk hatada kesilmesini önlemek için yalnızca "Yalnızca kendi kodum" onay kutusunun işaretini kaldırın **Araçlar, Seçenekler, hata ayıklama, genel**.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bcd3-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bcd3-108">Example</span></span>  
 <span data-ttu-id="7bcd3-109">Aşağıdaki örnekte, <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> yöntemi iki belirteci bir belirteç birleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="7bcd3-110">Bu, yalnızca bir iptal belirteci bağımsız değişken olarak ele yöntemlere geçirilen belirteç sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="7bcd3-111">Örnek bir yöntem den sınıf ve sınıf içinde oluşturulan bir belirteç dışında geçirilen bir belirteç uymanız gerekir, yaygın bir senaryo gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="7bcd3-112">Ne zaman bağlı belirteci oluşturur bir <xref:System.OperationCanceledException>, özel durum geçirilen belirteç bağlı, öncül belirteçlerin değil ya da belirtecidir.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="7bcd3-113">Hangi belirteçleri iptal edildi belirlemek için doğrudan öncül belirteçleri durumunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="7bcd3-114">Bu örnekte, <xref:System.AggregateException> hiçbir zaman durumun oluşturulması gerekir, ancak burada çünkü yakalandı gerçek dünya senaryolarında yanı sıra diğer tüm özel durumlar <xref:System.OperationCanceledException> görev temsilciden durum içinde sarmalanmış bir <xref:System.AggregateException>.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bcd3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bcd3-115">See also</span></span>

- [<span data-ttu-id="7bcd3-116">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="7bcd3-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
