---
title: 1014 - ScheduleCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 84203735-478d-42d8-a320-c175dbddcb38
ms.openlocfilehash: 50b00a49ea73dcbe09e8f4c4195cbce8c1cbf615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33510373"
---
# <a name="1014---schedulecompletionworkitem"></a><span data-ttu-id="56c97-102">1014 - ScheduleCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="56c97-102">1014 - ScheduleCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="56c97-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="56c97-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="56c97-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="56c97-104">ID</span></span>|<span data-ttu-id="56c97-105">1014</span><span class="sxs-lookup"><span data-stu-id="56c97-105">1014</span></span>|  
|<span data-ttu-id="56c97-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="56c97-106">Keywords</span></span>|<span data-ttu-id="56c97-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="56c97-107">WFRuntime</span></span>|  
|<span data-ttu-id="56c97-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="56c97-108">Level</span></span>|<span data-ttu-id="56c97-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="56c97-109">Verbose</span></span>|  
|<span data-ttu-id="56c97-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="56c97-110">Channel</span></span>|<span data-ttu-id="56c97-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="56c97-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="56c97-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56c97-112">Description</span></span>  
 <span data-ttu-id="56c97-113">Bir CompletionWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="56c97-113">Indicates a CompletionWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="56c97-114">İleti</span><span class="sxs-lookup"><span data-stu-id="56c97-114">Message</span></span>  
 <span data-ttu-id="56c97-115">Bir CompletionWorkItem üst etkinliği '%1', DisplayName zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="56c97-115">A CompletionWorkItem has been scheduled for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="56c97-116">'%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="56c97-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="56c97-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="56c97-117">Details</span></span>  
  
|<span data-ttu-id="56c97-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="56c97-118">Data Item Name</span></span>|<span data-ttu-id="56c97-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="56c97-119">Data Item Type</span></span>|<span data-ttu-id="56c97-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="56c97-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="56c97-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="56c97-121">ParentActivity</span></span>|<span data-ttu-id="56c97-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="56c97-122">xs:string</span></span>|<span data-ttu-id="56c97-123">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="56c97-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="56c97-124">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="56c97-124">ParentDisplayName</span></span>|<span data-ttu-id="56c97-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="56c97-125">xs:string</span></span>|<span data-ttu-id="56c97-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="56c97-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="56c97-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="56c97-127">ParentInstanceId</span></span>|<span data-ttu-id="56c97-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="56c97-128">xs:string</span></span>|<span data-ttu-id="56c97-129">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="56c97-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="56c97-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="56c97-130">CompletedActivity</span></span>|<span data-ttu-id="56c97-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="56c97-131">xs:string</span></span>|<span data-ttu-id="56c97-132">Tamamlanan etkinliğin türü adı.</span><span class="sxs-lookup"><span data-stu-id="56c97-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="56c97-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="56c97-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="56c97-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="56c97-134">xs:string</span></span>|<span data-ttu-id="56c97-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="56c97-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="56c97-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="56c97-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="56c97-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="56c97-137">xs:string</span></span>|<span data-ttu-id="56c97-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="56c97-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="56c97-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="56c97-139">AppDomain</span></span>|<span data-ttu-id="56c97-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="56c97-140">xs:string</span></span>|<span data-ttu-id="56c97-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="56c97-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
