---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924663"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="8bcc8-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="8bcc8-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="8bcc8-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8bcc8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8bcc8-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="8bcc8-104">ID</span></span>|<span data-ttu-id="8bcc8-105">1009</span><span class="sxs-lookup"><span data-stu-id="8bcc8-105">1009</span></span>|  
|<span data-ttu-id="8bcc8-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="8bcc8-106">Keywords</span></span>|<span data-ttu-id="8bcc8-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8bcc8-107">WFRuntime</span></span>|  
|<span data-ttu-id="8bcc8-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="8bcc8-108">Level</span></span>|<span data-ttu-id="8bcc8-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="8bcc8-109">Information</span></span>|  
|<span data-ttu-id="8bcc8-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="8bcc8-110">Channel</span></span>|<span data-ttu-id="8bcc8-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8bcc8-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8bcc8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bcc8-112">Description</span></span>  
 <span data-ttu-id="8bcc8-113">Yürütme için zamanlanan bir etkinlik gösterir.</span><span class="sxs-lookup"><span data-stu-id="8bcc8-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8bcc8-114">İleti</span><span class="sxs-lookup"><span data-stu-id="8bcc8-114">Message</span></span>  
 <span data-ttu-id="8bcc8-115">Üst etkinlik '%1', DisplayName: '%2', InstanceId: '%3' zamanlanmış alt etkinliği '%4', DisplayName: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="8bcc8-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8bcc8-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8bcc8-116">Details</span></span>  
  
|<span data-ttu-id="8bcc8-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8bcc8-117">Data Item Name</span></span>|<span data-ttu-id="8bcc8-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8bcc8-118">Data Item Type</span></span>|<span data-ttu-id="8bcc8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8bcc8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8bcc8-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="8bcc8-120">ParentActivity</span></span>|<span data-ttu-id="8bcc8-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="8bcc8-121">xs:string</span></span>|<span data-ttu-id="8bcc8-122">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="8bcc8-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="8bcc8-123">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="8bcc8-123">ParentDisplayName</span></span>|<span data-ttu-id="8bcc8-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="8bcc8-124">xs:string</span></span>|<span data-ttu-id="8bcc8-125">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="8bcc8-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="8bcc8-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="8bcc8-126">ParentInstanceId</span></span>|<span data-ttu-id="8bcc8-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="8bcc8-127">xs:string</span></span>|<span data-ttu-id="8bcc8-128">Üst etkinliği örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="8bcc8-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="8bcc8-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="8bcc8-129">ChildActivity</span></span>|<span data-ttu-id="8bcc8-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="8bcc8-130">xs:string</span></span>|<span data-ttu-id="8bcc8-131">Zamanlanmış bir alt etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="8bcc8-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="8bcc8-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="8bcc8-132">ChildDisplayName</span></span>|<span data-ttu-id="8bcc8-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="8bcc8-133">xs:string</span></span>|<span data-ttu-id="8bcc8-134">Zamanlanmış bir alt etkinlik görünen adı.</span><span class="sxs-lookup"><span data-stu-id="8bcc8-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="8bcc8-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="8bcc8-135">ChildInstanceId</span></span>|<span data-ttu-id="8bcc8-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="8bcc8-136">xs:string</span></span>|<span data-ttu-id="8bcc8-137">Zamanlanmış bir alt etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="8bcc8-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="8bcc8-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8bcc8-138">AppDomain</span></span>|<span data-ttu-id="8bcc8-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="8bcc8-139">xs:string</span></span>|<span data-ttu-id="8bcc8-140">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8bcc8-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
