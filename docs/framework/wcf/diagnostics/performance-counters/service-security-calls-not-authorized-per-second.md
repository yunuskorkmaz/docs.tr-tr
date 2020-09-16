---
title: 'Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 59e044f7c5946b32d959119939f972e081a8f57b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540497"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="429bb-102">Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı</span><span class="sxs-lookup"><span data-stu-id="429bb-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="429bb-103">Sayaç adı: saniye başına yetkilendirilmemiş güvenlik çağrısı</span><span class="sxs-lookup"><span data-stu-id="429bb-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="429bb-104">Description</span><span class="sxs-lookup"><span data-stu-id="429bb-104">Description</span></span>  
 <span data-ttu-id="429bb-105">Bir saniye içinde, geçerli bir kullanıcıdan gelen ve düzgün şekilde korunan, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş olan gelen ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="429bb-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="429bb-106">Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .</span><span class="sxs-lookup"><span data-stu-id="429bb-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="429bb-107">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="429bb-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="429bb-108">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="429bb-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
