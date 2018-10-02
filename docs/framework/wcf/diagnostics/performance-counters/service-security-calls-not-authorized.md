---
title: 'Hizmet: Güvenlik Çağrıları Yetkilendirilmedi'
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
author: BrucePerlerMS
ms.openlocfilehash: f90ed5746c8b798e55b7e300ba7ff63bbafdcac4
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48035889"
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="09f72-102">Hizmet: Güvenlik Çağrıları Yetkilendirilmedi</span><span class="sxs-lookup"><span data-stu-id="09f72-102">Service: Security Calls Not Authorized</span></span>
<span data-ttu-id="09f72-103">Sayaç adı: Güvenlik çağrıları yetkilendirilmedi.</span><span class="sxs-lookup"><span data-stu-id="09f72-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="09f72-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="09f72-104">Description</span></span>  
 <span data-ttu-id="09f72-105">Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="09f72-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="09f72-106">Bu, gelen ileti, geçerli bir kullanıcıdan gelen ve düzgün şekilde korumalı, ancak belirli görevleri gerçekleştirmek için kullanıcının yetkilendirilmeyen gösterir.</span><span class="sxs-lookup"><span data-stu-id="09f72-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
