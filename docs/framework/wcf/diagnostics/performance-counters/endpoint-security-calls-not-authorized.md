---
title: 'Uç Noktası: Güvenlik Çağrıları Yetkilendirilmedi'
ms.date: 03/30/2017
ms.assetid: d25095ff-9ff0-4c69-a674-4e6a9fe3f4dc
ms.openlocfilehash: 3979eec15759989b638e1cc813cb78a0c008c3a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256514"
---
# <a name="endpoint-security-calls-not-authorized"></a><span data-ttu-id="da496-102">Uç Noktası: Güvenlik Çağrıları Yetkilendirilmedi</span><span class="sxs-lookup"><span data-stu-id="da496-102">Endpoint: Security Calls Not Authorized</span></span>

<span data-ttu-id="da496-103">Sayaç adı: güvenlik çağrıları yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="da496-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="da496-104">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da496-104">Description</span></span>  

 <span data-ttu-id="da496-105">Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .</span><span class="sxs-lookup"><span data-stu-id="da496-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="da496-106">Gelen iletinin geçerli bir kullanıcıdan olduğunu ve düzgün şekilde korunduğunu gösterir, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş.</span><span class="sxs-lookup"><span data-stu-id="da496-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
