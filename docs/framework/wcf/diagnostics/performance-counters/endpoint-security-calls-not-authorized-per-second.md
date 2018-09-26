---
title: 'Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
ms.openlocfilehash: 4abea795eb196d339beec17fa7a171927aa85324
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47194067"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="19126-102">Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı</span><span class="sxs-lookup"><span data-stu-id="19126-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="19126-103">Sayaç adı: Saniyede yetkisiz güvenlik çağrısı.</span><span class="sxs-lookup"><span data-stu-id="19126-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="19126-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19126-104">Description</span></span>  
 <span data-ttu-id="19126-105">Geçerli bir kullanıcıdan ve düzgün şekilde korumalı saniyenin, ancak kullanıcı gelen ileti sayısı, belirli görevler gerçekleştirmek için yetkili değil.</span><span class="sxs-lookup"><span data-stu-id="19126-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="19126-106">Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="19126-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="19126-107">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="19126-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="19126-108">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="19126-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
