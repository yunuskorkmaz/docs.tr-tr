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
ms.openlocfilehash: dedb1dd389e2308ea8f70d71f057d17a45172517
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="9b751-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="9b751-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="9b751-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9b751-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9b751-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9b751-104">ID</span></span>|<span data-ttu-id="9b751-105">1008</span><span class="sxs-lookup"><span data-stu-id="9b751-105">1008</span></span>|  
|<span data-ttu-id="9b751-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9b751-106">Keywords</span></span>|<span data-ttu-id="9b751-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="9b751-107">WFRuntime</span></span>|  
|<span data-ttu-id="9b751-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9b751-108">Level</span></span>|<span data-ttu-id="9b751-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9b751-109">Information</span></span>|  
|<span data-ttu-id="9b751-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9b751-110">Channel</span></span>|<span data-ttu-id="9b751-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="9b751-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9b751-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b751-112">Description</span></span>  
 <span data-ttu-id="9b751-113">Bir iş akışı uygulaması kaldırıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="9b751-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9b751-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9b751-114">Message</span></span>  
 <span data-ttu-id="9b751-115">İş akışı örneği kimliği: '%1'. yüklenmeyen.</span><span class="sxs-lookup"><span data-stu-id="9b751-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9b751-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9b751-116">Details</span></span>  
  
|<span data-ttu-id="9b751-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9b751-117">Data Item Name</span></span>|<span data-ttu-id="9b751-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9b751-118">Data Item Type</span></span>|<span data-ttu-id="9b751-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b751-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9b751-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="9b751-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="9b751-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="9b751-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="9b751-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9b751-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9b751-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9b751-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
