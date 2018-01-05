---
title: "Güvenlik Çağrıları Yetkilendirilmedi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 641d627868c69a5ec63e1acc3f262d315341d0ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="e30f0-102">Güvenlik Çağrıları Yetkilendirilmedi</span><span class="sxs-lookup"><span data-stu-id="e30f0-102">Security Calls Not Authorized</span></span>
<span data-ttu-id="e30f0-103">Sayaç adı: Güvenlik çağrıları yetkilendirilmedi.</span><span class="sxs-lookup"><span data-stu-id="e30f0-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e30f0-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e30f0-104">Description</span></span>  
 <span data-ttu-id="e30f0-105">Bu sayaç artırılır zaman <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="e30f0-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="e30f0-106">Gelen ileti geçerli bir kullanıcıdan ve düzgün şekilde korumalı, ancak kullanıcının belirli görevleri gerçekleştirmek için yetkili değil gösterir.</span><span class="sxs-lookup"><span data-stu-id="e30f0-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
