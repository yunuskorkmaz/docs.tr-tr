---
title: 'Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d1fa297536cbac174e77b2d19b53b642a577f949
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474795"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="ad3a7-102">Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı</span><span class="sxs-lookup"><span data-stu-id="ad3a7-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="ad3a7-103">Sayaç adı: güvenlik çağrıları değil yetkili / saniye</span><span class="sxs-lookup"><span data-stu-id="ad3a7-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="ad3a7-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad3a7-104">Description</span></span>  
 <span data-ttu-id="ad3a7-105">Geçerli bir kullanıcıdan olan ve düzgün şekilde korumalı, bir saniye ancak kullanıcı gelen ileti sayısı belirli görevleri gerçekleştirmek için yetkili değil.</span><span class="sxs-lookup"><span data-stu-id="ad3a7-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="ad3a7-106">Bu sayaç artırılır zaman <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="ad3a7-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="ad3a7-107">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkId=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="ad3a7-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkId=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ad3a7-108">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="ad3a7-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
