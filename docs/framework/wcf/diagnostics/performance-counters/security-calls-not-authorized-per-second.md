---
title: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4970c6f6552163114b33a34ae87c6ed56b5e13
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703466"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="d17a2-102">Yetkilendirilmeyen Güvenlik Çağrısı/Saniye</span><span class="sxs-lookup"><span data-stu-id="d17a2-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="d17a2-103">Sayaç adı: Saniyede yetkisiz güvenlik çağrısı.</span><span class="sxs-lookup"><span data-stu-id="d17a2-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d17a2-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d17a2-104">Description</span></span>  
 <span data-ttu-id="d17a2-105">Bu işlemde ikinci bir kimlik doğrulamada başarısız olan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="d17a2-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="d17a2-106">Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="d17a2-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="d17a2-107">Bu, gelen ileti, geçerli bir kullanıcıdan gelen ve düzgün şekilde korumalı, ancak belirli görevleri gerçekleştirmek için kullanıcının yetkilendirilmeyen gösterir.</span><span class="sxs-lookup"><span data-stu-id="d17a2-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="d17a2-108">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="d17a2-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="d17a2-109">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="d17a2-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
