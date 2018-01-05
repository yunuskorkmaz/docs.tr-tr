---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe006534e0199888668145be9da3f964055cc464
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="f3135-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="f3135-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="f3135-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f3135-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3135-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f3135-104">ID</span></span>|<span data-ttu-id="f3135-105">1011</span><span class="sxs-lookup"><span data-stu-id="f3135-105">1011</span></span>|  
|<span data-ttu-id="f3135-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f3135-106">Keywords</span></span>|<span data-ttu-id="f3135-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f3135-107">WFRuntime</span></span>|  
|<span data-ttu-id="f3135-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f3135-108">Level</span></span>|<span data-ttu-id="f3135-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="f3135-109">Verbose</span></span>|  
|<span data-ttu-id="f3135-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f3135-110">Channel</span></span>|<span data-ttu-id="f3135-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f3135-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f3135-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3135-112">Description</span></span>  
 <span data-ttu-id="f3135-113">Bir ExecuteActivityWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3135-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f3135-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f3135-114">Message</span></span>  
 <span data-ttu-id="f3135-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="f3135-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f3135-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f3135-116">Details</span></span>  
  
|<span data-ttu-id="f3135-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f3135-117">Data Item Name</span></span>|<span data-ttu-id="f3135-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f3135-118">Data Item Type</span></span>|<span data-ttu-id="f3135-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3135-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f3135-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="f3135-120">Activity</span></span>|<span data-ttu-id="f3135-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="f3135-121">xs:string</span></span>|<span data-ttu-id="f3135-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="f3135-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="f3135-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="f3135-123">DisplayName</span></span>|<span data-ttu-id="f3135-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="f3135-124">xs:string</span></span>|<span data-ttu-id="f3135-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="f3135-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="f3135-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="f3135-126">InstanceId</span></span>|<span data-ttu-id="f3135-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="f3135-127">xs:string</span></span>|<span data-ttu-id="f3135-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="f3135-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f3135-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f3135-129">AppDomain</span></span>|<span data-ttu-id="f3135-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="f3135-130">xs:string</span></span>|<span data-ttu-id="f3135-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f3135-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
