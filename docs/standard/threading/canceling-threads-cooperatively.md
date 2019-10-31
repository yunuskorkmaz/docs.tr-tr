---
title: İş parçacıklarını işbirliği ile iptal etme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: 1d1433ecf39974bf9e68fe07b9d0818ac16fb544
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138123"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="5d8ed-102">İş parçacıklarını işbirliği ile iptal etme</span><span class="sxs-lookup"><span data-stu-id="5d8ed-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="5d8ed-103">.NET Framework 4 ' ten önce, .NET Framework başlatıldıktan sonra bir iş parçacığını iptal etmek için yerleşik bir yöntem sağlanmadı.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-103">Prior to the .NET Framework 4, the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="5d8ed-104">Ancak, .NET Framework 4 ' ü kullanmaya başlayarak, nesneleri <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya PLıNQ sorgularını iptal etmek için kullanabileceğiniz gibi, iş parçacıklarını iptal etmek için bir <xref:System.Threading.CancellationToken?displayProperty=nameWithType> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-104">However, starting with the .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="5d8ed-105"><xref:System.Threading.Thread?displayProperty=nameWithType> sınıfı, iptal belirteçleri için yerleşik destek sunmaz, ancak bir <xref:System.Threading.ParameterizedThreadStart> temsilcisi alan <xref:System.Threading.Thread> oluşturucusunu kullanarak bir iş parçacığı yordamına belirteç geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="5d8ed-106">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="5d8ed-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d8ed-107">See also</span></span>

- [<span data-ttu-id="5d8ed-108">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="5d8ed-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
