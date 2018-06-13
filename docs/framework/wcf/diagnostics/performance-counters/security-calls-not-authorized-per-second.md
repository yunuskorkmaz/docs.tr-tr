---
title: Yetkilendirilmeyen Güvenlik Çağrısı/Saniye
ms.date: 03/30/2017
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d8f04abc46a85f151108653b399c238e0275bf7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473561"
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="e0cbf-102">Yetkilendirilmeyen Güvenlik Çağrısı/Saniye</span><span class="sxs-lookup"><span data-stu-id="e0cbf-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="e0cbf-103">Sayaç adı: Saniyede yetkisiz güvenlik çağrısı.</span><span class="sxs-lookup"><span data-stu-id="e0cbf-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e0cbf-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e0cbf-104">Description</span></span>  
 <span data-ttu-id="e0cbf-105">Bu işlemde ikinci bir kimlik doğrulamada başarısız çağrı sayısı.</span><span class="sxs-lookup"><span data-stu-id="e0cbf-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="e0cbf-106">Bu sayaç artırılır zaman <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="e0cbf-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="e0cbf-107">Gelen ileti geçerli bir kullanıcıdan ve düzgün şekilde korumalı, ancak kullanıcının belirli görevleri gerçekleştirmek için yetkili değil gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0cbf-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="e0cbf-108">Bu sayaç, performans sayacı türü [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), değeri, aşağıdaki formül kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="e0cbf-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e0cbf-109">(1 - N 0 N) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="e0cbf-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
