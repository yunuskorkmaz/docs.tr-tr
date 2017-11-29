---
title: "Uç Noktası: Güvenlik Çağrıları Yetkilendirilmedi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 59922fad717ea464d8e023c25c8e17a3c17f1846
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="454fe-102">Uç Noktası: Güvenlik Çağrıları Yetkilendirilmedi</span><span class="sxs-lookup"><span data-stu-id="454fe-102">Endpoint: Security Calls Not Authorized</span></span>
<span data-ttu-id="454fe-103">Sayaç adı: Güvenlik çağrıları yetkilendirilmedi.</span><span class="sxs-lookup"><span data-stu-id="454fe-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="454fe-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="454fe-104">Description</span></span>  
 <span data-ttu-id="454fe-105">Bu sayaç artırılır zaman <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemi döndürür `false`.</span><span class="sxs-lookup"><span data-stu-id="454fe-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="454fe-106">Gelen ileti geçerli bir kullanıcıdan ve düzgün şekilde korumalı, ancak kullanıcının belirli görevleri gerçekleştirmek için yetkili değil gösterir.</span><span class="sxs-lookup"><span data-stu-id="454fe-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
