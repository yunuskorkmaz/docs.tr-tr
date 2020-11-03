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
ms.openlocfilehash: 36de18e976401dd0cde878852c064aa982b8acde
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188503"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="27c77-102">İş parçacıklarını işbirliği ile iptal etme</span><span class="sxs-lookup"><span data-stu-id="27c77-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="27c77-103">.NET Framework 4 ' ten önce, .NET, başlatıldıktan sonra bir iş parçacığını iptal etmek için yerleşik bir yöntem sağlamamıştı.</span><span class="sxs-lookup"><span data-stu-id="27c77-103">Prior to .NET Framework 4, .NET provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="27c77-104">Ancak, .NET Framework 4 ' ü kullanmaya başlayarak, <xref:System.Threading.CancellationToken?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya PLINQ sorgularını iptal etmek için bunları kullanabileceğiniz gibi, iş parçacıklarını iptal etmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27c77-104">However, starting with .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="27c77-105">Sınıfı, <xref:System.Threading.Thread?displayProperty=nameWithType> iptal belirteçleri için yerleşik destek sunmasa da, bir <xref:System.Threading.Thread> temsilciyi alan oluşturucuyu kullanarak bir iş parçacığı yordamına belirteç geçirebilirsiniz <xref:System.Threading.ParameterizedThreadStart> .</span><span class="sxs-lookup"><span data-stu-id="27c77-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="27c77-106">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="27c77-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="27c77-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27c77-107">See also</span></span>

- [<span data-ttu-id="27c77-108">Iş parçacıkları ve Iş parçacığı kullanma</span><span class="sxs-lookup"><span data-stu-id="27c77-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
