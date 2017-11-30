---
title: 1017 - ScheduleCancelActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 864546ab-d65c-4989-8fcb-537ba03a3cdd
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c6d348ec18b4d5eff7156d1e9809eb793ac1681d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="b5421-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="b5421-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b5421-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b5421-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5421-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b5421-104">ID</span></span>|<span data-ttu-id="b5421-105">1017</span><span class="sxs-lookup"><span data-stu-id="b5421-105">1017</span></span>|  
|<span data-ttu-id="b5421-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="b5421-106">Keywords</span></span>|<span data-ttu-id="b5421-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b5421-107">WFRuntime</span></span>|  
|<span data-ttu-id="b5421-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b5421-108">Level</span></span>|<span data-ttu-id="b5421-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="b5421-109">Verbose</span></span>|  
|<span data-ttu-id="b5421-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b5421-110">Channel</span></span>|<span data-ttu-id="b5421-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b5421-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b5421-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5421-112">Description</span></span>  
 <span data-ttu-id="b5421-113">Bir CancelActivityWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5421-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b5421-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b5421-114">Message</span></span>  
 <span data-ttu-id="b5421-115">'%1', DisplayName etkinliği için bir CancelActivityWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="b5421-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b5421-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b5421-116">Details</span></span>  
  
|<span data-ttu-id="b5421-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b5421-117">Data Item Name</span></span>|<span data-ttu-id="b5421-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b5421-118">Data Item Type</span></span>|<span data-ttu-id="b5421-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5421-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b5421-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="b5421-120">Activity</span></span>|<span data-ttu-id="b5421-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="b5421-121">xs:string</span></span>|<span data-ttu-id="b5421-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="b5421-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="b5421-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="b5421-123">DisplayName</span></span>|<span data-ttu-id="b5421-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="b5421-124">xs:string</span></span>|<span data-ttu-id="b5421-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b5421-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="b5421-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="b5421-126">InstanceId</span></span>|<span data-ttu-id="b5421-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="b5421-127">xs:string</span></span>|<span data-ttu-id="b5421-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5421-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b5421-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b5421-129">AppDomain</span></span>|<span data-ttu-id="b5421-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="b5421-130">xs:string</span></span>|<span data-ttu-id="b5421-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b5421-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
