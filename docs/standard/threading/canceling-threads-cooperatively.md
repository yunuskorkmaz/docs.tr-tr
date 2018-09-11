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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd32deb9c8719a12b76aaea8ec91a17471cf18f9
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259866"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="3c87d-102">İş parçacıklarını işbirliği ile iptal etme</span><span class="sxs-lookup"><span data-stu-id="3c87d-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="3c87d-103">Önce .NET Framework 4 ve .NET Framework, başlatıldıktan sonra bir iş parçacığı işbirliği içerisinde devamlılığı iptal etmek için yerleşik bir yolu yoktur sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3c87d-103">Prior to the .NET Framework 4, the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="3c87d-104">Ancak, .NET Framework 4 ile başlayarak, kullanabileceğiniz bir <xref:System.Threading.CancellationToken?displayProperty=nameWithType> yalnızca bunları iptal etmek için kullanabileceğiniz gibi iş parçacıkları, iptal etmek için <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya PLINQ sorguları.</span><span class="sxs-lookup"><span data-stu-id="3c87d-104">However, starting with the .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="3c87d-105">Ancak <xref:System.Threading.Thread?displayProperty=nameWithType> sınıfı iptal belirteçleri için yerleşik destek sunmaz, bir iş parçacığı yordamı için bir belirteç kullanarak geçirebilirsiniz <xref:System.Threading.Thread> alan oluşturucu bir <xref:System.Threading.ParameterizedThreadStart> temsilci.</span><span class="sxs-lookup"><span data-stu-id="3c87d-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="3c87d-106">Aşağıdaki örnek bunun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3c87d-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="3c87d-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c87d-107">See also</span></span>

- [<span data-ttu-id="3c87d-108">İş Parçacıkları ve İş Parçacığı Oluşturmayı Kullanma</span><span class="sxs-lookup"><span data-stu-id="3c87d-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
