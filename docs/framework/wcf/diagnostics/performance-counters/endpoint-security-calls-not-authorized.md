---
title: 'Uç Noktası: Güvenlik Çağrıları Yetkilendirilmedi'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
ms.openlocfilehash: b37d4cd33c41c6e978dd82ca7ce6332302a843de
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198035"
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="0fdb6-102">Uç Noktası: Güvenlik Çağrıları Yetkilendirilmedi</span><span class="sxs-lookup"><span data-stu-id="0fdb6-102">Endpoint: Security Calls Not Authorized</span></span>
<span data-ttu-id="0fdb6-103">Sayaç adı: Güvenlik çağrıları yetkilendirilmedi.</span><span class="sxs-lookup"><span data-stu-id="0fdb6-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0fdb6-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fdb6-104">Description</span></span>  
 <span data-ttu-id="0fdb6-105">Bu sayaç artırılır, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="0fdb6-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="0fdb6-106">Bu, gelen ileti, geçerli bir kullanıcıdan gelen ve düzgün şekilde korumalı, ancak belirli görevleri gerçekleştirmek için kullanıcının yetkilendirilmeyen gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fdb6-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
