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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 498752bfc896891a43a6a2e7a8245c508795c1ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="100e5-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="100e5-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="100e5-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="100e5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="100e5-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="100e5-104">ID</span></span>|<span data-ttu-id="100e5-105">1011</span><span class="sxs-lookup"><span data-stu-id="100e5-105">1011</span></span>|  
|<span data-ttu-id="100e5-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="100e5-106">Keywords</span></span>|<span data-ttu-id="100e5-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="100e5-107">WFRuntime</span></span>|  
|<span data-ttu-id="100e5-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="100e5-108">Level</span></span>|<span data-ttu-id="100e5-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="100e5-109">Verbose</span></span>|  
|<span data-ttu-id="100e5-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="100e5-110">Channel</span></span>|<span data-ttu-id="100e5-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="100e5-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="100e5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="100e5-112">Description</span></span>  
 <span data-ttu-id="100e5-113">Bir ExecuteActivityWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="100e5-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="100e5-114">İleti</span><span class="sxs-lookup"><span data-stu-id="100e5-114">Message</span></span>  
 <span data-ttu-id="100e5-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="100e5-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="100e5-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="100e5-116">Details</span></span>  
  
|<span data-ttu-id="100e5-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="100e5-117">Data Item Name</span></span>|<span data-ttu-id="100e5-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="100e5-118">Data Item Type</span></span>|<span data-ttu-id="100e5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="100e5-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="100e5-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="100e5-120">Activity</span></span>|<span data-ttu-id="100e5-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="100e5-121">xs:string</span></span>|<span data-ttu-id="100e5-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="100e5-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="100e5-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="100e5-123">DisplayName</span></span>|<span data-ttu-id="100e5-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="100e5-124">xs:string</span></span>|<span data-ttu-id="100e5-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="100e5-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="100e5-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="100e5-126">InstanceId</span></span>|<span data-ttu-id="100e5-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="100e5-127">xs:string</span></span>|<span data-ttu-id="100e5-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="100e5-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="100e5-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="100e5-129">AppDomain</span></span>|<span data-ttu-id="100e5-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="100e5-130">xs:string</span></span>|<span data-ttu-id="100e5-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="100e5-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
