---
title: 1033 - StartRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 172b5346-9f3b-46ae-bc06-39872022376a
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0de8e45a592cae49060f976b28a7a7bcf8781265
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1033---startruntimeworkitem"></a><span data-ttu-id="3d985-102">1033 - StartRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="3d985-102">1033 - StartRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="3d985-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3d985-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3d985-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="3d985-104">ID</span></span>|<span data-ttu-id="3d985-105">1033</span><span class="sxs-lookup"><span data-stu-id="3d985-105">1033</span></span>|  
|<span data-ttu-id="3d985-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="3d985-106">Keywords</span></span>|<span data-ttu-id="3d985-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="3d985-107">WFRuntime</span></span>|  
|<span data-ttu-id="3d985-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="3d985-108">Level</span></span>|<span data-ttu-id="3d985-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="3d985-109">Verbose</span></span>|  
|<span data-ttu-id="3d985-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="3d985-110">Channel</span></span>|<span data-ttu-id="3d985-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="3d985-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3d985-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d985-112">Description</span></span>  
 <span data-ttu-id="3d985-113">Bir RuntimeWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d985-113">Indicates a RuntimeWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3d985-114">İleti</span><span class="sxs-lookup"><span data-stu-id="3d985-114">Message</span></span>  
 <span data-ttu-id="3d985-115">Bir çalışma zamanı iş öğesinin yürütülmesi etkinliği '%1', DisplayName başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="3d985-115">Starting execution of a runtime work item for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3d985-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3d985-116">Details</span></span>  
  
|<span data-ttu-id="3d985-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="3d985-117">Data Item Name</span></span>|<span data-ttu-id="3d985-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="3d985-118">Data Item Type</span></span>|<span data-ttu-id="3d985-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3d985-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3d985-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="3d985-120">Activity</span></span>|<span data-ttu-id="3d985-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="3d985-121">xs:string</span></span>|<span data-ttu-id="3d985-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="3d985-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="3d985-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="3d985-123">DisplayName</span></span>|<span data-ttu-id="3d985-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="3d985-124">xs:string</span></span>|<span data-ttu-id="3d985-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="3d985-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="3d985-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="3d985-126">InstanceId</span></span>|<span data-ttu-id="3d985-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="3d985-127">xs:string</span></span>|<span data-ttu-id="3d985-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="3d985-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="3d985-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3d985-129">AppDomain</span></span>|<span data-ttu-id="3d985-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="3d985-130">xs:string</span></span>|<span data-ttu-id="3d985-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="3d985-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
