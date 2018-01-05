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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b524f083c49f517c21c77da4f1d1488625a575b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="0c6e7-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="0c6e7-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="0c6e7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0c6e7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c6e7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="0c6e7-104">ID</span></span>|<span data-ttu-id="0c6e7-105">1017</span><span class="sxs-lookup"><span data-stu-id="0c6e7-105">1017</span></span>|  
|<span data-ttu-id="0c6e7-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="0c6e7-106">Keywords</span></span>|<span data-ttu-id="0c6e7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0c6e7-107">WFRuntime</span></span>|  
|<span data-ttu-id="0c6e7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="0c6e7-108">Level</span></span>|<span data-ttu-id="0c6e7-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="0c6e7-109">Verbose</span></span>|  
|<span data-ttu-id="0c6e7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="0c6e7-110">Channel</span></span>|<span data-ttu-id="0c6e7-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0c6e7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0c6e7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c6e7-112">Description</span></span>  
 <span data-ttu-id="0c6e7-113">Bir CancelActivityWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0c6e7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="0c6e7-114">Message</span></span>  
 <span data-ttu-id="0c6e7-115">'%1', DisplayName etkinliği için bir CancelActivityWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0c6e7-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0c6e7-116">Details</span></span>  
  
|<span data-ttu-id="0c6e7-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="0c6e7-117">Data Item Name</span></span>|<span data-ttu-id="0c6e7-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="0c6e7-118">Data Item Type</span></span>|<span data-ttu-id="0c6e7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c6e7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0c6e7-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="0c6e7-120">Activity</span></span>|<span data-ttu-id="0c6e7-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="0c6e7-121">xs:string</span></span>|<span data-ttu-id="0c6e7-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="0c6e7-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="0c6e7-123">DisplayName</span></span>|<span data-ttu-id="0c6e7-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="0c6e7-124">xs:string</span></span>|<span data-ttu-id="0c6e7-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="0c6e7-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="0c6e7-126">InstanceId</span></span>|<span data-ttu-id="0c6e7-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="0c6e7-127">xs:string</span></span>|<span data-ttu-id="0c6e7-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="0c6e7-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0c6e7-129">AppDomain</span></span>|<span data-ttu-id="0c6e7-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="0c6e7-130">xs:string</span></span>|<span data-ttu-id="0c6e7-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
