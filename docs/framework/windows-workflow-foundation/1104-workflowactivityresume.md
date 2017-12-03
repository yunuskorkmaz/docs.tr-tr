---
title: 1104 - WorkflowActivityResume
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 029b1832259451beb458f8cbed4b0a3c44fdc490
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1104---workflowactivityresume"></a><span data-ttu-id="c8c24-102">1104 - WorkflowActivityResume</span><span class="sxs-lookup"><span data-stu-id="c8c24-102">1104 - WorkflowActivityResume</span></span>
## <a name="properties"></a><span data-ttu-id="c8c24-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c8c24-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8c24-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c8c24-104">ID</span></span>|<span data-ttu-id="c8c24-105">1104</span><span class="sxs-lookup"><span data-stu-id="c8c24-105">1104</span></span>|  
|<span data-ttu-id="c8c24-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c8c24-106">Keywords</span></span>|<span data-ttu-id="c8c24-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c8c24-107">WFRuntime</span></span>|  
|<span data-ttu-id="c8c24-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c8c24-108">Level</span></span>|<span data-ttu-id="c8c24-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="c8c24-109">Information</span></span>|  
|<span data-ttu-id="c8c24-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c8c24-110">Channel</span></span>|<span data-ttu-id="c8c24-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="c8c24-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c8c24-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8c24-112">Description</span></span>  
 <span data-ttu-id="c8c24-113">Bir iş akışı etkinliği sürdürüldü gösterir.</span><span class="sxs-lookup"><span data-stu-id="c8c24-113">Indicates a workflow activity has been resumed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c8c24-114">İleti</span><span class="sxs-lookup"><span data-stu-id="c8c24-114">Message</span></span>  
 <span data-ttu-id="c8c24-115">İş akışı örneği kimliği: '%1' E2E etkinliği</span><span class="sxs-lookup"><span data-stu-id="c8c24-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="c8c24-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c8c24-116">Details</span></span>  
  
|<span data-ttu-id="c8c24-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c8c24-117">Data Item Name</span></span>|<span data-ttu-id="c8c24-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c8c24-118">Data Item Type</span></span>|<span data-ttu-id="c8c24-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c8c24-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c8c24-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="c8c24-120">WorkflowInstanceId</span></span>|<span data-ttu-id="c8c24-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="c8c24-121">xs:string</span></span>|<span data-ttu-id="c8c24-122">İş akışı örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="c8c24-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="c8c24-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c8c24-123">AppDomain</span></span>|<span data-ttu-id="c8c24-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="c8c24-124">xs:string</span></span>|<span data-ttu-id="c8c24-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c8c24-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
