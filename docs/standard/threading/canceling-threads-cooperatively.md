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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138123"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="a09e5-102">İş parçacıklarını işbirliği ile iptal etme</span><span class="sxs-lookup"><span data-stu-id="a09e5-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="a09e5-103">.NET Framework 4'ten önce,.NET Framework başlatıldıktan sonra bir iş parçacığının birlikte iptal ilerleilmesi için yerleşik bir yol sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="a09e5-103">Prior to the .NET Framework 4, the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="a09e5-104">Ancak, .NET Framework 4'ten başlayarak, nesneleri veya PLINQ sorgularını <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> iptal etmek için kullanabileceğiniz gibi, iş parçacıklarını iptal etmek için de a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a09e5-104">However, starting with the .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="a09e5-105"><xref:System.Threading.Thread?displayProperty=nameWithType> Sınıf iptal belirteçleri için yerleşik destek sunmasa da, <xref:System.Threading.ParameterizedThreadStart> temsilci alan oluşturucuyu <xref:System.Threading.Thread> kullanarak iş parçacığı yordamına bir belirteç geçirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a09e5-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="a09e5-106">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="a09e5-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="a09e5-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a09e5-107">See also</span></span>

- [<span data-ttu-id="a09e5-108">İş Parçacığı ve İş Parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="a09e5-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
