---
title: Güvenlik Çağrıları Yetkilendirilmedi
ms.date: 03/30/2017
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
ms.openlocfilehash: 492886a8e0083e8993b68ad710229113faf79e8d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198412"
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="21285-102">Güvenlik Çağrıları Yetkilendirilmedi</span><span class="sxs-lookup"><span data-stu-id="21285-102">Security Calls Not Authorized</span></span>
<span data-ttu-id="21285-103">Sayaç adı: Güvenlik çağrıları yetkilendirilmedi.</span><span class="sxs-lookup"><span data-stu-id="21285-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="21285-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21285-104">Description</span></span>  
 <span data-ttu-id="21285-105">Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="21285-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="21285-106">Bu, gelen ileti, geçerli bir kullanıcıdan gelen ve düzgün şekilde korumalı, ancak belirli görevleri gerçekleştirmek için kullanıcının yetkilendirilmeyen gösterir.</span><span class="sxs-lookup"><span data-stu-id="21285-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
