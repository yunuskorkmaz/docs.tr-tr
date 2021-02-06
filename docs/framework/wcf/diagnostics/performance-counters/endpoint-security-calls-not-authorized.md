---
description: 'Şu konuda daha fazla bilgi edinin: uç nokta: güvenlik çağrıları yetkilendirilmemiş'
title: 'Uç Noktası: Güvenlik Çağrıları Yetkilendirilmedi'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
ms.openlocfilehash: 258c984e8a7986594b6da6f5c2a8c030907f82ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99655480"
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="f91fc-103">Uç Noktası: Güvenlik Çağrıları Yetkilendirilmedi</span><span class="sxs-lookup"><span data-stu-id="f91fc-103">Endpoint: Security Calls Not Authorized</span></span>

<span data-ttu-id="f91fc-104">Sayaç adı: güvenlik çağrıları yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="f91fc-104">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f91fc-105">Description</span><span class="sxs-lookup"><span data-stu-id="f91fc-105">Description</span></span>  

 <span data-ttu-id="f91fc-106">Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .</span><span class="sxs-lookup"><span data-stu-id="f91fc-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="f91fc-107">Gelen iletinin geçerli bir kullanıcıdan olduğunu ve düzgün şekilde korunduğunu gösterir, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="f91fc-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
