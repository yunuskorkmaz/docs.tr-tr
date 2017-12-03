---
title: 1013 - CompleteExecuteActivityWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fc57b3-ef2f-48f0-a5de-b4e2c5c9ded7
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de9add3f537c1d8ff97c92892197598bcc7a4fe7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1013---completeexecuteactivityworkitem"></a><span data-ttu-id="b5bc7-102">1013 - CompleteExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="b5bc7-102">1013 - CompleteExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="b5bc7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b5bc7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5bc7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b5bc7-104">ID</span></span>|<span data-ttu-id="b5bc7-105">1013</span><span class="sxs-lookup"><span data-stu-id="b5bc7-105">1013</span></span>|  
|<span data-ttu-id="b5bc7-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="b5bc7-106">Keywords</span></span>|<span data-ttu-id="b5bc7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b5bc7-107">WFRuntime</span></span>|  
|<span data-ttu-id="b5bc7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b5bc7-108">Level</span></span>|<span data-ttu-id="b5bc7-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="b5bc7-109">Verbose</span></span>|  
|<span data-ttu-id="b5bc7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b5bc7-110">Channel</span></span>|<span data-ttu-id="b5bc7-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b5bc7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b5bc7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5bc7-112">Description</span></span>  
 <span data-ttu-id="b5bc7-113">Bir ExecuteActivityWorkItem tamamlandığını gösterir</span><span class="sxs-lookup"><span data-stu-id="b5bc7-113">Indicates an ExecuteActivityWorkItem has completed</span></span>  
  
## <a name="message"></a><span data-ttu-id="b5bc7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b5bc7-114">Message</span></span>  
 <span data-ttu-id="b5bc7-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-115">An ExecuteActivityWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b5bc7-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b5bc7-116">Details</span></span>  
  
|<span data-ttu-id="b5bc7-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b5bc7-117">Data Item Name</span></span>|<span data-ttu-id="b5bc7-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b5bc7-118">Data Item Type</span></span>|<span data-ttu-id="b5bc7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b5bc7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b5bc7-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="b5bc7-120">Activity</span></span>|<span data-ttu-id="b5bc7-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="b5bc7-121">xs:string</span></span>|<span data-ttu-id="b5bc7-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="b5bc7-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="b5bc7-123">DisplayName</span></span>|<span data-ttu-id="b5bc7-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="b5bc7-124">xs:string</span></span>|<span data-ttu-id="b5bc7-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="b5bc7-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="b5bc7-126">InstanceId</span></span>|<span data-ttu-id="b5bc7-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="b5bc7-127">xs:string</span></span>|<span data-ttu-id="b5bc7-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b5bc7-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b5bc7-129">AppDomain</span></span>|<span data-ttu-id="b5bc7-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="b5bc7-130">xs:string</span></span>|<span data-ttu-id="b5bc7-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b5bc7-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
