---
description: 'Hakkında daha fazla bilgi edinin: 1032-ScheduleRuntimeWorkItem'
title: 1032 - ScheduleRuntimeWorkItem
ms.date: 03/30/2017
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
ms.openlocfilehash: d96226b4ab0f856218d292c9c2481bca6c463c8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668051"
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="756b4-103">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="756b4-103">1032 - ScheduleRuntimeWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="756b4-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="756b4-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="756b4-105">ID</span><span class="sxs-lookup"><span data-stu-id="756b4-105">ID</span></span>|<span data-ttu-id="756b4-106">1032</span><span class="sxs-lookup"><span data-stu-id="756b4-106">1032</span></span>|  
|<span data-ttu-id="756b4-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="756b4-107">Keywords</span></span>|<span data-ttu-id="756b4-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="756b4-108">WFRuntime</span></span>|  
|<span data-ttu-id="756b4-109">Level</span><span class="sxs-lookup"><span data-stu-id="756b4-109">Level</span></span>|<span data-ttu-id="756b4-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="756b4-110">Verbose</span></span>|  
|<span data-ttu-id="756b4-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="756b4-111">Channel</span></span>|<span data-ttu-id="756b4-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="756b4-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="756b4-113">Description</span><span class="sxs-lookup"><span data-stu-id="756b4-113">Description</span></span>  

 <span data-ttu-id="756b4-114">Bir RuntimeWorkItem zamanlandığı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="756b4-114">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="756b4-115">İleti</span><span class="sxs-lookup"><span data-stu-id="756b4-115">Message</span></span>  

 <span data-ttu-id="756b4-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir çalışma zamanı çalışma öğesi zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="756b4-116">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="756b4-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="756b4-117">Details</span></span>  
  
|<span data-ttu-id="756b4-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="756b4-118">Data Item Name</span></span>|<span data-ttu-id="756b4-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="756b4-119">Data Item Type</span></span>|<span data-ttu-id="756b4-120">Description</span><span class="sxs-lookup"><span data-stu-id="756b4-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="756b4-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="756b4-121">Activity</span></span>|<span data-ttu-id="756b4-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="756b4-122">xs:string</span></span>|<span data-ttu-id="756b4-123">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="756b4-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="756b4-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="756b4-124">DisplayName</span></span>|<span data-ttu-id="756b4-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="756b4-125">xs:string</span></span>|<span data-ttu-id="756b4-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="756b4-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="756b4-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="756b4-127">InstanceId</span></span>|<span data-ttu-id="756b4-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="756b4-128">xs:string</span></span>|<span data-ttu-id="756b4-129">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="756b4-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="756b4-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="756b4-130">AppDomain</span></span>|<span data-ttu-id="756b4-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="756b4-131">xs:string</span></span>|<span data-ttu-id="756b4-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="756b4-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
