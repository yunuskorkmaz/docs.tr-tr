---
title: "Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c6f03321ed77392342cbc5ee3c9cd5480f2d0455
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="93229-102">Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı</span><span class="sxs-lookup"><span data-stu-id="93229-102">Service: Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="93229-103">Sayaç adı: güvenlik çağrıları değil yetkili / saniye</span><span class="sxs-lookup"><span data-stu-id="93229-103">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="93229-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93229-104">Description</span></span>  
 <span data-ttu-id="93229-105">Geçerli bir kullanıcıdan olan ve düzgün şekilde korumalı, bir saniye ancak kullanıcı gelen ileti sayısı belirli görevleri gerçekleştirmek için yetkili değil.</span><span class="sxs-lookup"><span data-stu-id="93229-105">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="93229-106">Bu sayaç artırılır zaman <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="93229-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="93229-107">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkId=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="93229-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkId=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="93229-108">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="93229-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
