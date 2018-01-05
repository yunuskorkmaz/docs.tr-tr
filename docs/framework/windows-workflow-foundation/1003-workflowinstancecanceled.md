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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b264450703090edfcf99f9584c16d33eb82a76e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="a9370-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="a9370-102">1003 - WorkflowInstanceCanceled</span></span>
## <a name="properties"></a><span data-ttu-id="a9370-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a9370-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a9370-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a9370-104">ID</span></span>|<span data-ttu-id="a9370-105">1003</span><span class="sxs-lookup"><span data-stu-id="a9370-105">1003</span></span>|  
|<span data-ttu-id="a9370-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a9370-106">Keywords</span></span>|<span data-ttu-id="a9370-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a9370-107">WFRuntime</span></span>|  
|<span data-ttu-id="a9370-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a9370-108">Level</span></span>|<span data-ttu-id="a9370-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="a9370-109">Information</span></span>|  
|<span data-ttu-id="a9370-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a9370-110">Channel</span></span>|<span data-ttu-id="a9370-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a9370-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a9370-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9370-112">Description</span></span>  
 <span data-ttu-id="a9370-113">Bir iş akışı örneği iptal edilmiş durumda tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a9370-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a9370-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a9370-114">Message</span></span>  
 <span data-ttu-id="a9370-115">İş akışı örneği kimliği: '%1' iptal edilmiş durumda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a9370-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a9370-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a9370-116">Details</span></span>  
  
|<span data-ttu-id="a9370-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a9370-117">Data Item Name</span></span>|<span data-ttu-id="a9370-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a9370-118">Data Item Type</span></span>|<span data-ttu-id="a9370-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a9370-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a9370-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="a9370-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="a9370-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="a9370-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="a9370-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a9370-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a9370-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a9370-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
