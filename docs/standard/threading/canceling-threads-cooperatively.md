---
description: 'Hakkında daha fazla bilgi edinin: iş parçacıklarını birlikte Iptal etme'
title: İş parçacıklarını işbirliği ile iptal etme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: e166e95f3b7e000b4ea57cbd690de439b2883123
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99675500"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="86519-103">İş parçacıklarını işbirliği ile iptal etme</span><span class="sxs-lookup"><span data-stu-id="86519-103">Canceling threads cooperatively</span></span>

<span data-ttu-id="86519-104">.NET Framework 4 ' ten önce, .NET, başlatıldıktan sonra bir iş parçacığını iptal etmek için yerleşik bir yöntem sağlamamıştı.</span><span class="sxs-lookup"><span data-stu-id="86519-104">Prior to .NET Framework 4, .NET provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="86519-105">Ancak, .NET Framework 4 ' ü kullanmaya başlayarak, <xref:System.Threading.CancellationToken?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya PLINQ sorgularını iptal etmek için bunları kullanabileceğiniz gibi, iş parçacıklarını iptal etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86519-105">However, starting with .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="86519-106">Sınıfı, <xref:System.Threading.Thread?displayProperty=nameWithType> iptal belirteçleri için yerleşik destek sunmasa da, bir <xref:System.Threading.Thread> temsilciyi alan oluşturucuyu kullanarak bir iş parçacığı yordamına belirteç geçirebilirsiniz <xref:System.Threading.ParameterizedThreadStart> .</span><span class="sxs-lookup"><span data-stu-id="86519-106">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="86519-107">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="86519-107">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="86519-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86519-108">See also</span></span>

- [<span data-ttu-id="86519-109">Iş parçacıkları ve Iş parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="86519-109">Using Threads and Threading</span></span>](using-threads-and-threading.md)
