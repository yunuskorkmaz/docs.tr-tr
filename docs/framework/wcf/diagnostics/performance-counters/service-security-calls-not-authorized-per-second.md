---
description: 'Şu konuda daha fazla bilgi edinin: hizmet: Yetkilendirmeyen güvenlik çağrısı/saniye'
title: 'Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı'
ms.date: 03/30/2017
ms.assetid: 1eeade5a-ea62-4757-b1f9-1b1b1746abd1
ms.openlocfilehash: 7203b62a1dd2f01aabd8502c992d357742ddc4e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99635707"
---
# <a name="service-security-calls-not-authorized-per-second"></a><span data-ttu-id="0ee17-103">Hizmet: Saniyede Yetkisiz Güvenlik Çağrısı</span><span class="sxs-lookup"><span data-stu-id="0ee17-103">Service: Security Calls Not Authorized Per Second</span></span>

<span data-ttu-id="0ee17-104">Sayaç adı: saniye başına yetkilendirilmemiş güvenlik çağrısı</span><span class="sxs-lookup"><span data-stu-id="0ee17-104">Counter name: Security Calls Not Authorized Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="0ee17-105">Description</span><span class="sxs-lookup"><span data-stu-id="0ee17-105">Description</span></span>  

 <span data-ttu-id="0ee17-106">Bir saniye içinde, geçerli bir kullanıcıdan gelen ve düzgün şekilde korunan, ancak kullanıcı belirli görevleri yapmak için yetkilendirilmemiş olan gelen ileti sayısı.</span><span class="sxs-lookup"><span data-stu-id="0ee17-106">Number of incoming messages in one second, which are from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="0ee17-107">Bu sayaç, <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> yöntemin döndürdüğü zaman artırılır `false` .</span><span class="sxs-lookup"><span data-stu-id="0ee17-107">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span>  
  
 <span data-ttu-id="0ee17-108">Bu sayaç, değeri aşağıdaki formül kullanılarak hesaplanan [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))performans sayacı türüdür.</span><span class="sxs-lookup"><span data-stu-id="0ee17-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0ee17-109">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="0ee17-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
