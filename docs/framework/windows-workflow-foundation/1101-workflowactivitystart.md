---
title: 1101 - WorkflowActivityStart
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8d89b6f41838ee89b503746be4020b93db0ac96e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="8606b-102">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="8606b-102">1101 - WorkflowActivityStart</span></span>
## <a name="properties"></a><span data-ttu-id="8606b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8606b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8606b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="8606b-104">ID</span></span>|<span data-ttu-id="8606b-105">1101</span><span class="sxs-lookup"><span data-stu-id="8606b-105">1101</span></span>|  
|<span data-ttu-id="8606b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="8606b-106">Keywords</span></span>|<span data-ttu-id="8606b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8606b-107">WFRuntime</span></span>|  
|<span data-ttu-id="8606b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="8606b-108">Level</span></span>|<span data-ttu-id="8606b-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="8606b-109">Information</span></span>|  
|<span data-ttu-id="8606b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="8606b-110">Channel</span></span>|<span data-ttu-id="8606b-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8606b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8606b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8606b-112">Description</span></span>  
 <span data-ttu-id="8606b-113">Bir iş akışı etkinliği başlatıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8606b-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8606b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="8606b-114">Message</span></span>  
 <span data-ttu-id="8606b-115">İş akışı örneği kimliği: '%1' E2E etkinliği</span><span class="sxs-lookup"><span data-stu-id="8606b-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="8606b-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8606b-116">Details</span></span>  
  
|<span data-ttu-id="8606b-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8606b-117">Data Item Name</span></span>|<span data-ttu-id="8606b-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8606b-118">Data Item Type</span></span>|<span data-ttu-id="8606b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8606b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8606b-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="8606b-120">WorkflowInstanceId</span></span>|<span data-ttu-id="8606b-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="8606b-121">xs:string</span></span>|<span data-ttu-id="8606b-122">İş akışı örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="8606b-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="8606b-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8606b-123">AppDomain</span></span>|<span data-ttu-id="8606b-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="8606b-124">xs:string</span></span>|<span data-ttu-id="8606b-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8606b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
