---
title: 1032 - ScheduleRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54688101-becf-42f3-80ca-f53a7b527620
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d2a150b9e9c78a9ce1f5e20b962a58ef2d5dde9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="9180e-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="9180e-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="9180e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9180e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9180e-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9180e-104">ID</span></span>|<span data-ttu-id="9180e-105">1032</span><span class="sxs-lookup"><span data-stu-id="9180e-105">1032</span></span>|  
|<span data-ttu-id="9180e-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9180e-106">Keywords</span></span>|<span data-ttu-id="9180e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9180e-107">WFRuntime</span></span>|  
|<span data-ttu-id="9180e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9180e-108">Level</span></span>|<span data-ttu-id="9180e-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="9180e-109">Verbose</span></span>|  
|<span data-ttu-id="9180e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9180e-110">Channel</span></span>|<span data-ttu-id="9180e-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9180e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9180e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9180e-112">Description</span></span>  
 <span data-ttu-id="9180e-113">Bir RuntimeWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="9180e-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9180e-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9180e-114">Message</span></span>  
 <span data-ttu-id="9180e-115">'%1', DisplayName etkinliği için bir çalışma zamanı iş öğesi zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="9180e-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9180e-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9180e-116">Details</span></span>  
  
|<span data-ttu-id="9180e-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9180e-117">Data Item Name</span></span>|<span data-ttu-id="9180e-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9180e-118">Data Item Type</span></span>|<span data-ttu-id="9180e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9180e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9180e-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="9180e-120">Activity</span></span>|<span data-ttu-id="9180e-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="9180e-121">xs:string</span></span>|<span data-ttu-id="9180e-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="9180e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="9180e-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="9180e-123">DisplayName</span></span>|<span data-ttu-id="9180e-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="9180e-124">xs:string</span></span>|<span data-ttu-id="9180e-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="9180e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="9180e-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="9180e-126">InstanceId</span></span>|<span data-ttu-id="9180e-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="9180e-127">xs:string</span></span>|<span data-ttu-id="9180e-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="9180e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="9180e-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9180e-129">AppDomain</span></span>|<span data-ttu-id="9180e-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="9180e-130">xs:string</span></span>|<span data-ttu-id="9180e-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9180e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
