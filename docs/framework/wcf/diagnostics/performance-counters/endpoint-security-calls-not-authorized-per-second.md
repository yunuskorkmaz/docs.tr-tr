---
title: 'Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: 5b289d7e026b481576bd7de186364773a57c17bc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256527"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="4572a-102">Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı</span><span class="sxs-lookup"><span data-stu-id="4572a-102">Endpoint: Security Calls Not Authorized Per Second</span></span>

<span data-ttu-id="4572a-103">Sayaç adı: saniye başına yetkilendirilmemiş güvenlik çağrısı.</span><span class="sxs-lookup"><span data-stu-id="4572a-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4572a-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4572a-104">Description</span></span>  

 <span data-ttu-id="4572a-105">Saniye içinde geçerli bir kullanıcıdan gelen ve düzgün şekilde korunan gelen ileti sayısı, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="4572a-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="4572a-106">Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .</span><span class="sxs-lookup"><span data-stu-id="4572a-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="4572a-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="4572a-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4572a-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="4572a-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
