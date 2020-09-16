---
title: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 8aed9f6b8c60c8aecd1b576c13a7063e3a492046
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552511"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="fd0ae-102">Yetkilendirilmeyen Güvenlik Çağrısı/Saniye</span><span class="sxs-lookup"><span data-stu-id="fd0ae-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="fd0ae-103">Sayaç adı: saniye başına yetkilendirilmemiş güvenlik çağrısı.</span><span class="sxs-lookup"><span data-stu-id="fd0ae-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fd0ae-104">Description</span><span class="sxs-lookup"><span data-stu-id="fd0ae-104">Description</span></span>  
 <span data-ttu-id="fd0ae-105">Bu işlemde yetkilendirilemeyen çağrı sayısı (saniye).</span><span class="sxs-lookup"><span data-stu-id="fd0ae-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="fd0ae-106">Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .</span><span class="sxs-lookup"><span data-stu-id="fd0ae-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="fd0ae-107">Gelen iletinin geçerli bir kullanıcıdan olduğunu ve düzgün şekilde korunduğunu gösterir, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="fd0ae-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="fd0ae-108">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="fd0ae-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fd0ae-109">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="fd0ae-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
