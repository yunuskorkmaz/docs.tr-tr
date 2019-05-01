---
title: 1010 - ActivityCompleted
ms.date: 03/30/2017
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
ms.openlocfilehash: 355281e6aa8f621bd2f9c0862e641fafec872750
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008377"
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="5936f-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="5936f-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="5936f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5936f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5936f-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="5936f-104">ID</span></span>|<span data-ttu-id="5936f-105">1010</span><span class="sxs-lookup"><span data-stu-id="5936f-105">1010</span></span>|  
|<span data-ttu-id="5936f-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="5936f-106">Keywords</span></span>|<span data-ttu-id="5936f-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5936f-107">WFRuntime</span></span>|  
|<span data-ttu-id="5936f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="5936f-108">Level</span></span>|<span data-ttu-id="5936f-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="5936f-109">Information</span></span>|  
|<span data-ttu-id="5936f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="5936f-110">Channel</span></span>|<span data-ttu-id="5936f-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5936f-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5936f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5936f-112">Description</span></span>  
 <span data-ttu-id="5936f-113">Bir etkinlik yürütmeyi tamamladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5936f-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5936f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="5936f-114">Message</span></span>  
 <span data-ttu-id="5936f-115">Etkinliği '%1', DisplayName: '%2', InstanceId: '%3' '%4' durumunda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="5936f-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5936f-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5936f-116">Details</span></span>  
  
|<span data-ttu-id="5936f-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="5936f-117">Data Item Name</span></span>|<span data-ttu-id="5936f-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="5936f-118">Data Item Type</span></span>|<span data-ttu-id="5936f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5936f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5936f-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="5936f-120">Activity</span></span>|<span data-ttu-id="5936f-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5936f-121">xs:string</span></span>|<span data-ttu-id="5936f-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="5936f-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="5936f-123">displayName</span><span class="sxs-lookup"><span data-stu-id="5936f-123">DisplayName</span></span>|<span data-ttu-id="5936f-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5936f-124">xs:string</span></span>|<span data-ttu-id="5936f-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="5936f-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="5936f-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="5936f-126">InstanceId</span></span>|<span data-ttu-id="5936f-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5936f-127">xs:string</span></span>|<span data-ttu-id="5936f-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="5936f-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5936f-129">Durum</span><span class="sxs-lookup"><span data-stu-id="5936f-129">State</span></span>|<span data-ttu-id="5936f-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="5936f-130">xs:string</span></span>|<span data-ttu-id="5936f-131">Etkinliğin durumu.</span><span class="sxs-lookup"><span data-stu-id="5936f-131">The state of the activity.</span></span>|  
|<span data-ttu-id="5936f-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5936f-132">AppDomain</span></span>|<span data-ttu-id="5936f-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="5936f-133">xs:string</span></span>|<span data-ttu-id="5936f-134">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="5936f-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
