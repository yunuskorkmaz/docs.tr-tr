---
title: 1019 - CompleteCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75a4a1ab-e5a3-4f4e-88e4-d19806e671d7
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9f8af4486d4659afd4c98016a6f88719271f1a1b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1019---completecancelactivityworkitem"></a><span data-ttu-id="0f8be-102">1019 - CompleteCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="0f8be-102">1019 - CompleteCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0f8be-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0f8be-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f8be-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="0f8be-104">ID</span></span>|<span data-ttu-id="0f8be-105">1019</span><span class="sxs-lookup"><span data-stu-id="0f8be-105">1019</span></span>|  
|<span data-ttu-id="0f8be-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="0f8be-106">Keywords</span></span>|<span data-ttu-id="0f8be-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0f8be-107">WFRuntime</span></span>|  
|<span data-ttu-id="0f8be-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="0f8be-108">Level</span></span>|<span data-ttu-id="0f8be-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="0f8be-109">Verbose</span></span>|  
|<span data-ttu-id="0f8be-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="0f8be-110">Channel</span></span>|<span data-ttu-id="0f8be-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0f8be-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0f8be-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f8be-112">Description</span></span>  
 <span data-ttu-id="0f8be-113">Bir CancelActivityWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0f8be-113">Indicates a CancelActivityWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0f8be-114">İleti</span><span class="sxs-lookup"><span data-stu-id="0f8be-114">Message</span></span>  
 <span data-ttu-id="0f8be-115">'%1', DisplayName etkinliği için bir CancelActivityWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="0f8be-115">A CancelActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0f8be-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0f8be-116">Details</span></span>  
  
|<span data-ttu-id="0f8be-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="0f8be-117">Data Item Name</span></span>|<span data-ttu-id="0f8be-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="0f8be-118">Data Item Type</span></span>|<span data-ttu-id="0f8be-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f8be-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0f8be-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="0f8be-120">Activity</span></span>|<span data-ttu-id="0f8be-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="0f8be-121">xs:string</span></span>|<span data-ttu-id="0f8be-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="0f8be-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="0f8be-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="0f8be-123">DisplayName</span></span>|<span data-ttu-id="0f8be-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="0f8be-124">xs:string</span></span>|<span data-ttu-id="0f8be-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="0f8be-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="0f8be-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="0f8be-126">InstanceId</span></span>|<span data-ttu-id="0f8be-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="0f8be-127">xs:string</span></span>|<span data-ttu-id="0f8be-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="0f8be-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0f8be-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0f8be-129">AppDomain</span></span>|<span data-ttu-id="0f8be-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="0f8be-130">xs:string</span></span>|<span data-ttu-id="0f8be-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0f8be-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
