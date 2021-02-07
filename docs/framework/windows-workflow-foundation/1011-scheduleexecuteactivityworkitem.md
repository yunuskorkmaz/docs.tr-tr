---
description: 'Hakkında daha fazla bilgi edinin: 1011-Scheduleexecuteactivityworkıtem'
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 81010390de2ad01ec3063f2ac89608b97dcb713e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703360"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="a262e-103">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="a262e-103">1011 - ScheduleExecuteActivityWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="a262e-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a262e-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a262e-105">ID</span><span class="sxs-lookup"><span data-stu-id="a262e-105">ID</span></span>|<span data-ttu-id="a262e-106">1011</span><span class="sxs-lookup"><span data-stu-id="a262e-106">1011</span></span>|  
|<span data-ttu-id="a262e-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a262e-107">Keywords</span></span>|<span data-ttu-id="a262e-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a262e-108">WFRuntime</span></span>|  
|<span data-ttu-id="a262e-109">Level</span><span class="sxs-lookup"><span data-stu-id="a262e-109">Level</span></span>|<span data-ttu-id="a262e-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="a262e-110">Verbose</span></span>|  
|<span data-ttu-id="a262e-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="a262e-111">Channel</span></span>|<span data-ttu-id="a262e-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="a262e-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a262e-113">Description</span><span class="sxs-lookup"><span data-stu-id="a262e-113">Description</span></span>  

 <span data-ttu-id="a262e-114">Bir ExecuteActivityWorkItem zamanlandığı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="a262e-114">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a262e-115">İleti</span><span class="sxs-lookup"><span data-stu-id="a262e-115">Message</span></span>  

 <span data-ttu-id="a262e-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir ExecuteActivityWorkItem zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="a262e-116">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a262e-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a262e-117">Details</span></span>  
  
|<span data-ttu-id="a262e-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a262e-118">Data Item Name</span></span>|<span data-ttu-id="a262e-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a262e-119">Data Item Type</span></span>|<span data-ttu-id="a262e-120">Description</span><span class="sxs-lookup"><span data-stu-id="a262e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a262e-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="a262e-121">Activity</span></span>|<span data-ttu-id="a262e-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="a262e-122">xs:string</span></span>|<span data-ttu-id="a262e-123">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="a262e-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="a262e-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a262e-124">DisplayName</span></span>|<span data-ttu-id="a262e-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="a262e-125">xs:string</span></span>|<span data-ttu-id="a262e-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a262e-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="a262e-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="a262e-127">InstanceId</span></span>|<span data-ttu-id="a262e-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="a262e-128">xs:string</span></span>|<span data-ttu-id="a262e-129">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="a262e-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="a262e-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a262e-130">AppDomain</span></span>|<span data-ttu-id="a262e-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="a262e-131">xs:string</span></span>|<span data-ttu-id="a262e-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a262e-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
