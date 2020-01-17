---
title: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 2986ba241ef9b6c110a4742f77320469cdf5f07a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163936"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="fd92a-102">Yetkilendirilmeyen Güvenlik Çağrısı/Saniye</span><span class="sxs-lookup"><span data-stu-id="fd92a-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="fd92a-103">Sayaç adı: saniye başına yetkilendirilmemiş güvenlik çağrısı.</span><span class="sxs-lookup"><span data-stu-id="fd92a-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fd92a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fd92a-104">Description</span></span>  
 <span data-ttu-id="fd92a-105">Bu işlemde yetkilendirilemeyen çağrı sayısı (saniye).</span><span class="sxs-lookup"><span data-stu-id="fd92a-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="fd92a-106"><xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi `false`döndürdüğünde Bu sayaç artırılır.</span><span class="sxs-lookup"><span data-stu-id="fd92a-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="fd92a-107">Gelen iletinin geçerli bir kullanıcıdan olduğunu ve düzgün şekilde korunduğunu gösterir, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="fd92a-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="fd92a-108">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="fd92a-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fd92a-109">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="fd92a-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
