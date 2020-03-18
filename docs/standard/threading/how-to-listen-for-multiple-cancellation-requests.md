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
ms.openlocfilehash: e35472040b6ee1263ebc4c4968fa1822045a2064
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138004"
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a><span data-ttu-id="ddf9f-102">Nasıl Yapılır: Birden Çok İptal İsteğini Dinleme</span><span class="sxs-lookup"><span data-stu-id="ddf9f-102">How to: Listen for Multiple Cancellation Requests</span></span>
<span data-ttu-id="ddf9f-103">Bu örnek, iki iptal jetonunun aynı anda nasıl dinleyeceğinigösterir, böylece belirteç isterse işlemi iptal edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-103">This example shows how to listen to two cancellation tokens simultaneously so that you can cancel an operation if either token requests it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ddf9f-104">"Yalnızca Kodum" etkinleştirildiğinde, bazı durumlarda Visual Studio özel durumu oluşturan satırda kırılır ve "kullanıcı kodu tarafından işlenmemiş özel durum" yazan bir hata iletisi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-104">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="ddf9f-105">Bu hata iyi huylu.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-105">This error is benign.</span></span> <span data-ttu-id="ddf9f-106">Devam etmek için F5 tuşuna basabilir ve aşağıdaki örneklerde gösterilen özel durum işleme davranışını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-106">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="ddf9f-107">Visual Studio'nun ilk hatayı kırmasını önlemek **için, Araçlar, Seçenekler, Hata Ayıklama, Genel**altında "Sadece Kodum" onay kutusunun işaretlerini kaldırın.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-107">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddf9f-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddf9f-108">Example</span></span>  
 <span data-ttu-id="ddf9f-109">Aşağıdaki örnekte, <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> yöntem bir belirteç içine iki belirteçleri birleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-109">In the following example, the <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> method is used to join two tokens into one token.</span></span> <span data-ttu-id="ddf9f-110">Bu, belirteci bir argüman olarak sadece bir iptal belirteci almak yöntemleri geçirilebilir sağlar.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-110">This enables the token to be passed to methods that take just one cancellation token as an argument.</span></span> <span data-ttu-id="ddf9f-111">Örnek, bir yöntemin hem sınıfın dışından geçirilen bir belirteci hem de sınıf içinde oluşturulan bir belirteci gözlemlemesi gereken ortak bir senaryoyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-111">The example demonstrates a common scenario in which a method must observe both a token passed in from outside the class, and a token generated inside the class.</span></span>  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 <span data-ttu-id="ddf9f-112">Bağlı belirteç bir <xref:System.OperationCanceledException>, özel durum geçirilir belirteci, önceki belirteçleri ya da bağlantılı belirteçleri atar.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-112">When the linked token throws an <xref:System.OperationCanceledException>, the token that is passed to the exception is the linked token, not either of the predecessor tokens.</span></span> <span data-ttu-id="ddf9f-113">Belirteçlerden hangisinin iptal edildiğini belirlemek için, doğrudan öncül belirteçlerin durumunu denetleyin.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-113">To determine which of the tokens was canceled, check the status of the predecessor tokens directly.</span></span>  
  
 <span data-ttu-id="ddf9f-114">Bu örnekte, <xref:System.AggregateException> asla atılmamalıdır, ancak burada yakalanır çünkü gerçek dünya senaryolarında <xref:System.OperationCanceledException> görev temsilcisinden atılan diğer özel <xref:System.AggregateException>durumlar bir .</span><span class="sxs-lookup"><span data-stu-id="ddf9f-114">In this example, <xref:System.AggregateException> should never be thrown, but it is caught here because in real-world scenarios any other exceptions besides <xref:System.OperationCanceledException> that are thrown from the task delegate are wrapped in a <xref:System.AggregateException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddf9f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddf9f-115">See also</span></span>

- [<span data-ttu-id="ddf9f-116">Yönetilen İş Parçacıklarında İptal</span><span class="sxs-lookup"><span data-stu-id="ddf9f-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
