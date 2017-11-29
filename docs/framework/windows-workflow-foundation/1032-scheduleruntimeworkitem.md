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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4de69b1fc2647d7723db8aebb02942938db7478f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="abb47-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="abb47-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="abb47-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="abb47-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="abb47-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="abb47-104">ID</span></span>|<span data-ttu-id="abb47-105">1032</span><span class="sxs-lookup"><span data-stu-id="abb47-105">1032</span></span>|  
|<span data-ttu-id="abb47-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="abb47-106">Keywords</span></span>|<span data-ttu-id="abb47-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="abb47-107">WFRuntime</span></span>|  
|<span data-ttu-id="abb47-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="abb47-108">Level</span></span>|<span data-ttu-id="abb47-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="abb47-109">Verbose</span></span>|  
|<span data-ttu-id="abb47-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="abb47-110">Channel</span></span>|<span data-ttu-id="abb47-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="abb47-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="abb47-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abb47-112">Description</span></span>  
 <span data-ttu-id="abb47-113">Bir RuntimeWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="abb47-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="abb47-114">İleti</span><span class="sxs-lookup"><span data-stu-id="abb47-114">Message</span></span>  
 <span data-ttu-id="abb47-115">'%1', DisplayName etkinliği için bir çalışma zamanı iş öğesi zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="abb47-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="abb47-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="abb47-116">Details</span></span>  
  
|<span data-ttu-id="abb47-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="abb47-117">Data Item Name</span></span>|<span data-ttu-id="abb47-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="abb47-118">Data Item Type</span></span>|<span data-ttu-id="abb47-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abb47-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="abb47-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="abb47-120">Activity</span></span>|<span data-ttu-id="abb47-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="abb47-121">xs:string</span></span>|<span data-ttu-id="abb47-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="abb47-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="abb47-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="abb47-123">DisplayName</span></span>|<span data-ttu-id="abb47-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="abb47-124">xs:string</span></span>|<span data-ttu-id="abb47-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="abb47-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="abb47-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="abb47-126">InstanceId</span></span>|<span data-ttu-id="abb47-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="abb47-127">xs:string</span></span>|<span data-ttu-id="abb47-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="abb47-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="abb47-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="abb47-129">AppDomain</span></span>|<span data-ttu-id="abb47-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="abb47-130">xs:string</span></span>|<span data-ttu-id="abb47-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="abb47-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
