---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982273"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="43e07-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="43e07-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="43e07-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="43e07-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43e07-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="43e07-104">ID</span></span>|<span data-ttu-id="43e07-105">1014</span><span class="sxs-lookup"><span data-stu-id="43e07-105">1014</span></span>|  
|<span data-ttu-id="43e07-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="43e07-106">Keywords</span></span>|<span data-ttu-id="43e07-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="43e07-107">WFRuntime</span></span>|  
|<span data-ttu-id="43e07-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="43e07-108">Level</span></span>|<span data-ttu-id="43e07-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="43e07-109">Verbose</span></span>|  
|<span data-ttu-id="43e07-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="43e07-110">Channel</span></span>|<span data-ttu-id="43e07-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="43e07-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="43e07-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43e07-112">Description</span></span>  
 <span data-ttu-id="43e07-113">Bir CompletionWorkItem zamanlandı gösterir.</span><span class="sxs-lookup"><span data-stu-id="43e07-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="43e07-114">İleti</span><span class="sxs-lookup"><span data-stu-id="43e07-114">Message</span></span>  
 <span data-ttu-id="43e07-115">Bir CompletionWorkItem üst etkinliği '%1', DisplayName zamanlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="43e07-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="43e07-116">'%4', DisplayName etkinliği tamamlandı: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="43e07-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="43e07-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="43e07-117">Details</span></span>  
  
|<span data-ttu-id="43e07-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="43e07-118">Data Item Name</span></span>|<span data-ttu-id="43e07-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="43e07-119">Data Item Type</span></span>|<span data-ttu-id="43e07-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43e07-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="43e07-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="43e07-121">ParentActivity</span></span>|<span data-ttu-id="43e07-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="43e07-122">xs:string</span></span>|<span data-ttu-id="43e07-123">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="43e07-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="43e07-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="43e07-124">ParentDisplayName</span></span>|<span data-ttu-id="43e07-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="43e07-125">xs:string</span></span>|<span data-ttu-id="43e07-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="43e07-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="43e07-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="43e07-127">ParentInstanceId</span></span>|<span data-ttu-id="43e07-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="43e07-128">xs:string</span></span>|<span data-ttu-id="43e07-129">Üst etkinliği örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="43e07-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="43e07-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="43e07-130">CompletedActivity</span></span>|<span data-ttu-id="43e07-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="43e07-131">xs:string</span></span>|<span data-ttu-id="43e07-132">Tamamlanan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="43e07-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="43e07-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="43e07-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="43e07-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="43e07-134">xs:string</span></span>|<span data-ttu-id="43e07-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="43e07-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="43e07-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="43e07-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="43e07-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="43e07-137">xs:string</span></span>|<span data-ttu-id="43e07-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="43e07-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="43e07-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="43e07-139">AppDomain</span></span>|<span data-ttu-id="43e07-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="43e07-140">xs:string</span></span>|<span data-ttu-id="43e07-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="43e07-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
