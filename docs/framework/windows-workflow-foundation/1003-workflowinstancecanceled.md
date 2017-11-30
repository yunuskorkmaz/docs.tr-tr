---
title: 1003 - WorkflowInstanceCanceled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b287c99453724f855a51e9a1b8068337dd5e373
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="6cbbd-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="6cbbd-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="6cbbd-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6cbbd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6cbbd-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="6cbbd-104">ID</span></span>|<span data-ttu-id="6cbbd-105">1003</span><span class="sxs-lookup"><span data-stu-id="6cbbd-105">1003</span></span>|  
|<span data-ttu-id="6cbbd-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="6cbbd-106">Keywords</span></span>|<span data-ttu-id="6cbbd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="6cbbd-107">WFRuntime</span></span>|  
|<span data-ttu-id="6cbbd-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="6cbbd-108">Level</span></span>|<span data-ttu-id="6cbbd-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="6cbbd-109">Information</span></span>|  
|<span data-ttu-id="6cbbd-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="6cbbd-110">Channel</span></span>|<span data-ttu-id="6cbbd-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="6cbbd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6cbbd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cbbd-112">Description</span></span>  
 <span data-ttu-id="6cbbd-113">Bir iş akışı örneği iptal edilmiş durumda tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6cbbd-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6cbbd-114">İleti</span><span class="sxs-lookup"><span data-stu-id="6cbbd-114">Message</span></span>  
 <span data-ttu-id="6cbbd-115">İş akışı örneği kimliği: '%1' iptal edilmiş durumda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="6cbbd-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6cbbd-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6cbbd-116">Details</span></span>  
  
|<span data-ttu-id="6cbbd-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="6cbbd-117">Data Item Name</span></span>|<span data-ttu-id="6cbbd-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="6cbbd-118">Data Item Type</span></span>|<span data-ttu-id="6cbbd-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6cbbd-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6cbbd-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="6cbbd-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="6cbbd-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="6cbbd-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="6cbbd-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6cbbd-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6cbbd-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="6cbbd-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
