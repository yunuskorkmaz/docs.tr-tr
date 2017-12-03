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
ms.openlocfilehash: a632d59ddd75b375ff5e828a9f35aeecb0118f1c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1017---schedulecancelactivityworkitem"></a><span data-ttu-id="7495a-102">1017 - ScheduleCancelActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="7495a-102">1017 - ScheduleCancelActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="7495a-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7495a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7495a-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="7495a-104">ID</span></span>|<span data-ttu-id="7495a-105">1017</span><span class="sxs-lookup"><span data-stu-id="7495a-105">1017</span></span>|  
|<span data-ttu-id="7495a-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="7495a-106">Keywords</span></span>|<span data-ttu-id="7495a-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="7495a-107">WFRuntime</span></span>|  
|<span data-ttu-id="7495a-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="7495a-108">Level</span></span>|<span data-ttu-id="7495a-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="7495a-109">Verbose</span></span>|  
|<span data-ttu-id="7495a-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="7495a-110">Channel</span></span>|<span data-ttu-id="7495a-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="7495a-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7495a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7495a-112">Description</span></span>  
 <span data-ttu-id="7495a-113">Bir CancelActivityWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="7495a-113">Indicates a CancelActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7495a-114">İleti</span><span class="sxs-lookup"><span data-stu-id="7495a-114">Message</span></span>  
 <span data-ttu-id="7495a-115">'%1', DisplayName etkinliği için bir CancelActivityWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="7495a-115">A CancelActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7495a-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7495a-116">Details</span></span>  
  
|<span data-ttu-id="7495a-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="7495a-117">Data Item Name</span></span>|<span data-ttu-id="7495a-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="7495a-118">Data Item Type</span></span>|<span data-ttu-id="7495a-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7495a-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7495a-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="7495a-120">Activity</span></span>|<span data-ttu-id="7495a-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="7495a-121">xs:string</span></span>|<span data-ttu-id="7495a-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="7495a-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="7495a-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="7495a-123">DisplayName</span></span>|<span data-ttu-id="7495a-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="7495a-124">xs:string</span></span>|<span data-ttu-id="7495a-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="7495a-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="7495a-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="7495a-126">InstanceId</span></span>|<span data-ttu-id="7495a-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="7495a-127">xs:string</span></span>|<span data-ttu-id="7495a-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="7495a-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="7495a-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7495a-129">AppDomain</span></span>|<span data-ttu-id="7495a-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="7495a-130">xs:string</span></span>|<span data-ttu-id="7495a-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="7495a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
