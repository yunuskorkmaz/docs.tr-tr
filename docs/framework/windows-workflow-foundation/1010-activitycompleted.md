---
title: 1010 - ActivityCompleted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d256284e-3fd2-4c33-82f4-abb617575706
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1378ddd1550db614c9eddc44f79b19ff94ed585c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1010---activitycompleted"></a><span data-ttu-id="1b04e-102">1010 - ActivityCompleted</span><span class="sxs-lookup"><span data-stu-id="1b04e-102">1010 - ActivityCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="1b04e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1b04e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1b04e-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="1b04e-104">ID</span></span>|<span data-ttu-id="1b04e-105">1010</span><span class="sxs-lookup"><span data-stu-id="1b04e-105">1010</span></span>|  
|<span data-ttu-id="1b04e-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="1b04e-106">Keywords</span></span>|<span data-ttu-id="1b04e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1b04e-107">WFRuntime</span></span>|  
|<span data-ttu-id="1b04e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1b04e-108">Level</span></span>|<span data-ttu-id="1b04e-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="1b04e-109">Information</span></span>|  
|<span data-ttu-id="1b04e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1b04e-110">Channel</span></span>|<span data-ttu-id="1b04e-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1b04e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1b04e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b04e-112">Description</span></span>  
 <span data-ttu-id="1b04e-113">Bir etkinlik yürütmeyi tamamladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b04e-113">Indicates an activity has completed execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1b04e-114">İleti</span><span class="sxs-lookup"><span data-stu-id="1b04e-114">Message</span></span>  
 <span data-ttu-id="1b04e-115">Etkinlik '%1', DisplayName: '%2', örnek kimliği: '%3' '%4' durumunda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1b04e-115">Activity '%1', DisplayName: '%2', InstanceId: '%3' has completed in the '%4' state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1b04e-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1b04e-116">Details</span></span>  
  
|<span data-ttu-id="1b04e-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1b04e-117">Data Item Name</span></span>|<span data-ttu-id="1b04e-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1b04e-118">Data Item Type</span></span>|<span data-ttu-id="1b04e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b04e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1b04e-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="1b04e-120">Activity</span></span>|<span data-ttu-id="1b04e-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="1b04e-121">xs:string</span></span>|<span data-ttu-id="1b04e-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="1b04e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="1b04e-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="1b04e-123">DisplayName</span></span>|<span data-ttu-id="1b04e-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="1b04e-124">xs:string</span></span>|<span data-ttu-id="1b04e-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="1b04e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="1b04e-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="1b04e-126">InstanceId</span></span>|<span data-ttu-id="1b04e-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="1b04e-127">xs:string</span></span>|<span data-ttu-id="1b04e-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="1b04e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="1b04e-129">Durum</span><span class="sxs-lookup"><span data-stu-id="1b04e-129">State</span></span>|<span data-ttu-id="1b04e-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="1b04e-130">xs:string</span></span>|<span data-ttu-id="1b04e-131">Etkinlik durumu.</span><span class="sxs-lookup"><span data-stu-id="1b04e-131">The state of the activity.</span></span>|  
|<span data-ttu-id="1b04e-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1b04e-132">AppDomain</span></span>|<span data-ttu-id="1b04e-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="1b04e-133">xs:string</span></span>|<span data-ttu-id="1b04e-134">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1b04e-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
