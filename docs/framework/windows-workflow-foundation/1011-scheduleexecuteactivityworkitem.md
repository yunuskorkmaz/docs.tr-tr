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
ms.openlocfilehash: ec89acb9d83a28ac280db7c3d536bfe63669fa97
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="a271d-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="a271d-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="a271d-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a271d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a271d-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a271d-104">ID</span></span>|<span data-ttu-id="a271d-105">1011</span><span class="sxs-lookup"><span data-stu-id="a271d-105">1011</span></span>|  
|<span data-ttu-id="a271d-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a271d-106">Keywords</span></span>|<span data-ttu-id="a271d-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a271d-107">WFRuntime</span></span>|  
|<span data-ttu-id="a271d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a271d-108">Level</span></span>|<span data-ttu-id="a271d-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="a271d-109">Verbose</span></span>|  
|<span data-ttu-id="a271d-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a271d-110">Channel</span></span>|<span data-ttu-id="a271d-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a271d-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a271d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a271d-112">Description</span></span>  
 <span data-ttu-id="a271d-113">Bir ExecuteActivityWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="a271d-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a271d-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a271d-114">Message</span></span>  
 <span data-ttu-id="a271d-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="a271d-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a271d-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a271d-116">Details</span></span>  
  
|<span data-ttu-id="a271d-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a271d-117">Data Item Name</span></span>|<span data-ttu-id="a271d-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a271d-118">Data Item Type</span></span>|<span data-ttu-id="a271d-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a271d-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a271d-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="a271d-120">Activity</span></span>|<span data-ttu-id="a271d-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="a271d-121">xs:string</span></span>|<span data-ttu-id="a271d-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="a271d-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="a271d-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="a271d-123">DisplayName</span></span>|<span data-ttu-id="a271d-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="a271d-124">xs:string</span></span>|<span data-ttu-id="a271d-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a271d-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="a271d-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="a271d-126">InstanceId</span></span>|<span data-ttu-id="a271d-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="a271d-127">xs:string</span></span>|<span data-ttu-id="a271d-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="a271d-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a271d-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a271d-129">AppDomain</span></span>|<span data-ttu-id="a271d-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="a271d-130">xs:string</span></span>|<span data-ttu-id="a271d-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a271d-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
