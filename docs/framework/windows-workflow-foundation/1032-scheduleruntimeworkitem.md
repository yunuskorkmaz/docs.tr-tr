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
ms.workload: dotnet
ms.openlocfilehash: 81cc73a5ab58e90f1a0ee5bdaf9a491d20206fb3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1032---scheduleruntimeworkitem"></a><span data-ttu-id="136cb-102">1032 - ScheduleRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="136cb-102">1032 - ScheduleRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="136cb-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="136cb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="136cb-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="136cb-104">ID</span></span>|<span data-ttu-id="136cb-105">1032</span><span class="sxs-lookup"><span data-stu-id="136cb-105">1032</span></span>|  
|<span data-ttu-id="136cb-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="136cb-106">Keywords</span></span>|<span data-ttu-id="136cb-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="136cb-107">WFRuntime</span></span>|  
|<span data-ttu-id="136cb-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="136cb-108">Level</span></span>|<span data-ttu-id="136cb-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="136cb-109">Verbose</span></span>|  
|<span data-ttu-id="136cb-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="136cb-110">Channel</span></span>|<span data-ttu-id="136cb-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="136cb-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="136cb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="136cb-112">Description</span></span>  
 <span data-ttu-id="136cb-113">Bir RuntimeWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="136cb-113">Indicates a RuntimeWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="136cb-114">İleti</span><span class="sxs-lookup"><span data-stu-id="136cb-114">Message</span></span>  
 <span data-ttu-id="136cb-115">'%1', DisplayName etkinliği için bir çalışma zamanı iş öğesi zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="136cb-115">A runtime work item has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="136cb-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="136cb-116">Details</span></span>  
  
|<span data-ttu-id="136cb-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="136cb-117">Data Item Name</span></span>|<span data-ttu-id="136cb-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="136cb-118">Data Item Type</span></span>|<span data-ttu-id="136cb-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="136cb-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="136cb-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="136cb-120">Activity</span></span>|<span data-ttu-id="136cb-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="136cb-121">xs:string</span></span>|<span data-ttu-id="136cb-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="136cb-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="136cb-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="136cb-123">DisplayName</span></span>|<span data-ttu-id="136cb-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="136cb-124">xs:string</span></span>|<span data-ttu-id="136cb-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="136cb-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="136cb-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="136cb-126">InstanceId</span></span>|<span data-ttu-id="136cb-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="136cb-127">xs:string</span></span>|<span data-ttu-id="136cb-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="136cb-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="136cb-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="136cb-129">AppDomain</span></span>|<span data-ttu-id="136cb-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="136cb-130">xs:string</span></span>|<span data-ttu-id="136cb-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="136cb-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
