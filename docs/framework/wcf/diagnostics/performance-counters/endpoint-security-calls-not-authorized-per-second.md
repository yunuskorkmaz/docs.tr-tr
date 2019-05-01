---
title: 'Uç noktası: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
ms.openlocfilehash: c62bec570daf8b107ca0540871eb6eac43ca2d7e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61951120"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="3ca68-102">Uç noktası: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye</span><span class="sxs-lookup"><span data-stu-id="3ca68-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="3ca68-103">Sayaç adı: Saniyede yetkilendirilmeyen güvenlik çağrıları.</span><span class="sxs-lookup"><span data-stu-id="3ca68-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3ca68-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3ca68-104">Description</span></span>  
 <span data-ttu-id="3ca68-105">Geçerli bir kullanıcıdan ve düzgün şekilde korumalı saniyenin, ancak kullanıcı gelen ileti sayısı, belirli görevler gerçekleştirmek için yetkili değil.</span><span class="sxs-lookup"><span data-stu-id="3ca68-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="3ca68-106">Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="3ca68-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="3ca68-107">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="3ca68-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="3ca68-108">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="3ca68-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
