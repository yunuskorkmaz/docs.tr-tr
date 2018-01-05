---
title: 1008 - WorkflowApplicationUnloaded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26491c1e2b20f4285aaedbcd12947cad3562f041
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="425e9-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="425e9-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="425e9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="425e9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="425e9-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="425e9-104">ID</span></span>|<span data-ttu-id="425e9-105">1008</span><span class="sxs-lookup"><span data-stu-id="425e9-105">1008</span></span>|  
|<span data-ttu-id="425e9-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="425e9-106">Keywords</span></span>|<span data-ttu-id="425e9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="425e9-107">WFRuntime</span></span>|  
|<span data-ttu-id="425e9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="425e9-108">Level</span></span>|<span data-ttu-id="425e9-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="425e9-109">Information</span></span>|  
|<span data-ttu-id="425e9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="425e9-110">Channel</span></span>|<span data-ttu-id="425e9-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="425e9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="425e9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="425e9-112">Description</span></span>  
 <span data-ttu-id="425e9-113">Bir iş akışı uygulaması kaldırıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="425e9-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="425e9-114">İleti</span><span class="sxs-lookup"><span data-stu-id="425e9-114">Message</span></span>  
 <span data-ttu-id="425e9-115">İş akışı örneği kimliği: '%1'. yüklenmeyen.</span><span class="sxs-lookup"><span data-stu-id="425e9-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="425e9-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="425e9-116">Details</span></span>  
  
|<span data-ttu-id="425e9-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="425e9-117">Data Item Name</span></span>|<span data-ttu-id="425e9-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="425e9-118">Data Item Type</span></span>|<span data-ttu-id="425e9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="425e9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="425e9-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="425e9-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="425e9-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="425e9-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="425e9-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="425e9-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="425e9-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="425e9-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
