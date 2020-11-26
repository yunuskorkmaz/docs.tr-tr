---
title: 'Hizmet: Güvenlik Çağrıları Yetkilendirilmedi'
ms.date: 03/30/2017
ms.assetid: 3024b20a-5250-4bd1-a38c-c6d79f89610b
ms.openlocfilehash: 32b0a62ecf9364270f5580787b7e129af5ac80b2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236916"
---
# <a name="service-security-calls-not-authorized"></a><span data-ttu-id="c10a2-102">Hizmet: Güvenlik Çağrıları Yetkilendirilmedi</span><span class="sxs-lookup"><span data-stu-id="c10a2-102">Service: Security Calls Not Authorized</span></span>

<span data-ttu-id="c10a2-103">Sayaç adı: güvenlik çağrıları yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="c10a2-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c10a2-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c10a2-104">Description</span></span>  

 <span data-ttu-id="c10a2-105">Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .</span><span class="sxs-lookup"><span data-stu-id="c10a2-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="c10a2-106">Gelen iletinin geçerli bir kullanıcıdan olduğunu ve düzgün şekilde korunduğunu gösterir, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="c10a2-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
