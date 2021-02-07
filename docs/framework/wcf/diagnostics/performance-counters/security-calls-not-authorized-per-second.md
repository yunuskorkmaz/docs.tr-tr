---
description: Hakkında daha fazla bilgi için bkz. saniyedeki yetkilendirilmemiş güvenlik çağrısı
title: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
ms.openlocfilehash: 60e1baf2b1ed1f3dc502608e6667266608010f0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716217"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="c9d2f-103">Yetkilendirilmeyen Güvenlik Çağrısı/Saniye</span><span class="sxs-lookup"><span data-stu-id="c9d2f-103">Security Calls Not Authorized Per Second</span></span>

<span data-ttu-id="c9d2f-104">Sayaç adı: saniye başına yetkilendirilmemiş güvenlik çağrısı.</span><span class="sxs-lookup"><span data-stu-id="c9d2f-104">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c9d2f-105">Description</span><span class="sxs-lookup"><span data-stu-id="c9d2f-105">Description</span></span>  

 <span data-ttu-id="c9d2f-106">Bu işlemde yetkilendirilemeyen çağrı sayısı (saniye).</span><span class="sxs-lookup"><span data-stu-id="c9d2f-106">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="c9d2f-107">Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .</span><span class="sxs-lookup"><span data-stu-id="c9d2f-107">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="c9d2f-108">Gelen iletinin geçerli bir kullanıcıdan olduğunu ve düzgün şekilde korunduğunu gösterir, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="c9d2f-108">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="c9d2f-109">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="c9d2f-109">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c9d2f-110">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="c9d2f-110">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
