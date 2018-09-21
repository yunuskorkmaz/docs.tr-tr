---
title: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4d4970c6f6552163114b33a34ae87c6ed56b5e13
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46488597"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="0c3a6-102">Yetkilendirilmeyen Güvenlik Çağrısı/Saniye</span><span class="sxs-lookup"><span data-stu-id="0c3a6-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="0c3a6-103">Sayaç adı: Saniyede yetkisiz güvenlik çağrısı.</span><span class="sxs-lookup"><span data-stu-id="0c3a6-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0c3a6-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c3a6-104">Description</span></span>  
 <span data-ttu-id="0c3a6-105">Bu işlemde ikinci bir kimlik doğrulamada başarısız olan çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="0c3a6-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="0c3a6-106">Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="0c3a6-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="0c3a6-107">Bu, gelen ileti, geçerli bir kullanıcıdan gelen ve düzgün şekilde korumalı, ancak belirli görevleri gerçekleştirmek için kullanıcının yetkilendirilmeyen gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c3a6-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="0c3a6-108">Bu sayaç performans sayacı türüdür [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), değeri aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="0c3a6-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0c3a6-109">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="0c3a6-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
