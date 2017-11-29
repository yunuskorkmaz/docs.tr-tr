---
title: 1034 - CompleteRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63ab145b8a0688a7f7bbf7dbcbe8dfe612eab294
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="f293b-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="f293b-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="f293b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f293b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f293b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f293b-104">ID</span></span>|<span data-ttu-id="f293b-105">1034</span><span class="sxs-lookup"><span data-stu-id="f293b-105">1034</span></span>|  
|<span data-ttu-id="f293b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f293b-106">Keywords</span></span>|<span data-ttu-id="f293b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f293b-107">WFRuntime</span></span>|  
|<span data-ttu-id="f293b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f293b-108">Level</span></span>|<span data-ttu-id="f293b-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="f293b-109">Verbose</span></span>|  
|<span data-ttu-id="f293b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f293b-110">Channel</span></span>|<span data-ttu-id="f293b-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f293b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f293b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f293b-112">Description</span></span>  
 <span data-ttu-id="f293b-113">Bir RuntimeWorkItem tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f293b-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f293b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f293b-114">Message</span></span>  
 <span data-ttu-id="f293b-115">Bir çalışma zamanı iş öğesi etkinliği için '%1', DisplayName tamamlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="f293b-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f293b-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f293b-116">Details</span></span>  
  
|<span data-ttu-id="f293b-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f293b-117">Data Item Name</span></span>|<span data-ttu-id="f293b-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f293b-118">Data Item Type</span></span>|<span data-ttu-id="f293b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f293b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f293b-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="f293b-120">Activity</span></span>|<span data-ttu-id="f293b-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="f293b-121">xs:string</span></span>|<span data-ttu-id="f293b-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="f293b-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="f293b-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="f293b-123">DisplayName</span></span>|<span data-ttu-id="f293b-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="f293b-124">xs:string</span></span>|<span data-ttu-id="f293b-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="f293b-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="f293b-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="f293b-126">InstanceId</span></span>|<span data-ttu-id="f293b-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="f293b-127">xs:string</span></span>|<span data-ttu-id="f293b-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="f293b-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="f293b-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f293b-129">AppDomain</span></span>|<span data-ttu-id="f293b-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="f293b-130">xs:string</span></span>|<span data-ttu-id="f293b-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f293b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
