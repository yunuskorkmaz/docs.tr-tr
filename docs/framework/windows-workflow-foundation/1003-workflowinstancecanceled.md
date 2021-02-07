---
description: 'Hakkında daha fazla bilgi edinin: 1003-Workflowcecanceled'
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: ef7b7c6849e96866204fe53deadce8302d18e0d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703385"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="c0f42-103">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="c0f42-103">1003 - WorkflowInstanceCanceled</span></span>

## <a name="properties"></a><span data-ttu-id="c0f42-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c0f42-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c0f42-105">ID</span><span class="sxs-lookup"><span data-stu-id="c0f42-105">ID</span></span>|<span data-ttu-id="c0f42-106">1003</span><span class="sxs-lookup"><span data-stu-id="c0f42-106">1003</span></span>|  
|<span data-ttu-id="c0f42-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="c0f42-107">Keywords</span></span>|<span data-ttu-id="c0f42-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c0f42-108">WFRuntime</span></span>|  
|<span data-ttu-id="c0f42-109">Level</span><span class="sxs-lookup"><span data-stu-id="c0f42-109">Level</span></span>|<span data-ttu-id="c0f42-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="c0f42-110">Information</span></span>|  
|<span data-ttu-id="c0f42-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="c0f42-111">Channel</span></span>|<span data-ttu-id="c0f42-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="c0f42-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c0f42-113">Description</span><span class="sxs-lookup"><span data-stu-id="c0f42-113">Description</span></span>  

 <span data-ttu-id="c0f42-114">Iptal edilen durumda bir iş akışı örneğinin tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0f42-114">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c0f42-115">İleti</span><span class="sxs-lookup"><span data-stu-id="c0f42-115">Message</span></span>  

 <span data-ttu-id="c0f42-116">WorkflowInstance kimliği: ' %1 ' Iptal edildi durumunda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c0f42-116">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c0f42-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c0f42-117">Details</span></span>  
  
|<span data-ttu-id="c0f42-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c0f42-118">Data Item Name</span></span>|<span data-ttu-id="c0f42-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c0f42-119">Data Item Type</span></span>|<span data-ttu-id="c0f42-120">Description</span><span class="sxs-lookup"><span data-stu-id="c0f42-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c0f42-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="c0f42-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="c0f42-122">İş akışının örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="c0f42-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="c0f42-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c0f42-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c0f42-124">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c0f42-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
