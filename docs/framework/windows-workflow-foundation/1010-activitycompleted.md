---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: d0ebf32ec1d5fe5b34ffe650d5547891be0eb665
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239919"
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="80559-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="80559-102">1010 - ActivityCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="80559-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="80559-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="80559-104">ID</span><span class="sxs-lookup"><span data-stu-id="80559-104">ID</span></span>|<span data-ttu-id="80559-105">1010</span><span class="sxs-lookup"><span data-stu-id="80559-105">1010</span></span>|  
|<span data-ttu-id="80559-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="80559-106">Keywords</span></span>|<span data-ttu-id="80559-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="80559-107">WFRuntime</span></span>|  
|<span data-ttu-id="80559-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="80559-108">Level</span></span>|<span data-ttu-id="80559-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="80559-109">Information</span></span>|  
|<span data-ttu-id="80559-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="80559-110">Channel</span></span>|<span data-ttu-id="80559-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="80559-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="80559-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80559-112">Description</span></span>  

 <span data-ttu-id="80559-113">Bir etkinliğin yürütmenin tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="80559-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="80559-114">İleti</span><span class="sxs-lookup"><span data-stu-id="80559-114">Message</span></span>  

 <span data-ttu-id="80559-115">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si ' %4 ' durumunda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="80559-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="80559-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="80559-116">Details</span></span>  
  
|<span data-ttu-id="80559-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="80559-117">Data Item Name</span></span>|<span data-ttu-id="80559-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="80559-118">Data Item Type</span></span>|<span data-ttu-id="80559-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="80559-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="80559-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="80559-120">Activity</span></span>|<span data-ttu-id="80559-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="80559-121">xs:string</span></span>|<span data-ttu-id="80559-122">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="80559-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="80559-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="80559-123">DisplayName</span></span>|<span data-ttu-id="80559-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="80559-124">xs:string</span></span>|<span data-ttu-id="80559-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="80559-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="80559-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="80559-126">InstanceId</span></span>|<span data-ttu-id="80559-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="80559-127">xs:string</span></span>|<span data-ttu-id="80559-128">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="80559-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="80559-129">Durum</span><span class="sxs-lookup"><span data-stu-id="80559-129">State</span></span>|<span data-ttu-id="80559-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="80559-130">xs:string</span></span>|<span data-ttu-id="80559-131">Etkinliğin durumu.</span><span class="sxs-lookup"><span data-stu-id="80559-131">The state of the activity.</span></span>|  
|<span data-ttu-id="80559-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="80559-132">AppDomain</span></span>|<span data-ttu-id="80559-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="80559-133">xs:string</span></span>|<span data-ttu-id="80559-134">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="80559-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
