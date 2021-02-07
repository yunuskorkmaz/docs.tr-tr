---
description: 'Şu konuda daha fazla bilgi edinin: hizmet: güvenlik çağrıları yetkilendirilmemiş'
title: 'Hizmet: Güvenlik Çağrıları Yetkilendirilmedi'
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
ms.openlocfilehash: 2185f478d534696ea308e06d8411df6888420914
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735757"
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="6f32b-103">Hizmet: Güvenlik Çağrıları Yetkilendirilmedi</span><span class="sxs-lookup"><span data-stu-id="6f32b-103">Service: Security Calls Not Authorized</span></span>

<span data-ttu-id="6f32b-104">Sayaç adı: güvenlik çağrıları yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="6f32b-104">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6f32b-105">Description</span><span class="sxs-lookup"><span data-stu-id="6f32b-105">Description</span></span>  

 <span data-ttu-id="6f32b-106">Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .</span><span class="sxs-lookup"><span data-stu-id="6f32b-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="6f32b-107">Gelen iletinin geçerli bir kullanıcıdan olduğunu ve düzgün şekilde korunduğunu gösterir, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="6f32b-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
