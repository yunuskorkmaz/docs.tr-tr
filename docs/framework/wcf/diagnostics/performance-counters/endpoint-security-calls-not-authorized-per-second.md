---
title: 'Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı'
ms.date: 03/30/2017
ms.assetid: c8a1547b-986b-45c1-b302-dea0cd4b516d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0fd7c3ab7abcc374c4ef89f9f5a0650647cf97a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471710"
---
# <a name="endpoint-security-calls-not-authorized-per-second"></a><span data-ttu-id="87b10-102">Uç Noktası: Saniyede Yetkisiz Güvenlik Çağrısı</span><span class="sxs-lookup"><span data-stu-id="87b10-102">Endpoint: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="87b10-103">Sayaç adı: Saniyede yetkisiz güvenlik çağrısı.</span><span class="sxs-lookup"><span data-stu-id="87b10-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="87b10-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87b10-104">Description</span></span>  
 <span data-ttu-id="87b10-105">Geçerli bir kullanıcıdan ve düzgün şekilde korumalı saniyenin, ancak kullanıcı gelen ileti sayısı belirli görevleri gerçekleştirmek için yetkili değil.</span><span class="sxs-lookup"><span data-stu-id="87b10-105">Number of incoming messages in a second that are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="87b10-106">Bu sayaç artırılır zaman <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="87b10-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="87b10-107">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="87b10-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="87b10-108">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="87b10-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
