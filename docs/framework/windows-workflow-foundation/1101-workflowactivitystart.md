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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7687e747d22c4726f11a6d17aa8b719897ab8473
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="e88d1-102">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="e88d1-102">1101 - WorkflowActivityStart</span></span>
## <a name="properties"></a><span data-ttu-id="e88d1-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e88d1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e88d1-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e88d1-104">ID</span></span>|<span data-ttu-id="e88d1-105">1101</span><span class="sxs-lookup"><span data-stu-id="e88d1-105">1101</span></span>|  
|<span data-ttu-id="e88d1-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e88d1-106">Keywords</span></span>|<span data-ttu-id="e88d1-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e88d1-107">WFRuntime</span></span>|  
|<span data-ttu-id="e88d1-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e88d1-108">Level</span></span>|<span data-ttu-id="e88d1-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="e88d1-109">Information</span></span>|  
|<span data-ttu-id="e88d1-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e88d1-110">Channel</span></span>|<span data-ttu-id="e88d1-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="e88d1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e88d1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e88d1-112">Description</span></span>  
 <span data-ttu-id="e88d1-113">Bir iş akışı etkinliği başlatıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e88d1-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e88d1-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e88d1-114">Message</span></span>  
 <span data-ttu-id="e88d1-115">İş akışı örneği kimliği: '%1' E2E etkinliği</span><span class="sxs-lookup"><span data-stu-id="e88d1-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="e88d1-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e88d1-116">Details</span></span>  
  
|<span data-ttu-id="e88d1-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e88d1-117">Data Item Name</span></span>|<span data-ttu-id="e88d1-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e88d1-118">Data Item Type</span></span>|<span data-ttu-id="e88d1-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e88d1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e88d1-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="e88d1-120">WorkflowInstanceId</span></span>|<span data-ttu-id="e88d1-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="e88d1-121">xs:string</span></span>|<span data-ttu-id="e88d1-122">İş akışı örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="e88d1-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="e88d1-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e88d1-123">AppDomain</span></span>|<span data-ttu-id="e88d1-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="e88d1-124">xs:string</span></span>|<span data-ttu-id="e88d1-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e88d1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
