---
title: 1006 - WorkflowApplicationUnhandledException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 842d6bb6172eed5f7382633119045ea7507fb955
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="2c943-102">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="2c943-102">1006 - WorkflowApplicationUnhandledException</span></span>
## <a name="properties"></a><span data-ttu-id="2c943-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2c943-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c943-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="2c943-104">ID</span></span>|<span data-ttu-id="2c943-105">1006</span><span class="sxs-lookup"><span data-stu-id="2c943-105">1006</span></span>|  
|<span data-ttu-id="2c943-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="2c943-106">Keywords</span></span>|<span data-ttu-id="2c943-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2c943-107">WFRuntime</span></span>|  
|<span data-ttu-id="2c943-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2c943-108">Level</span></span>|<span data-ttu-id="2c943-109">Hata</span><span class="sxs-lookup"><span data-stu-id="2c943-109">Error</span></span>|  
|<span data-ttu-id="2c943-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2c943-110">Channel</span></span>|<span data-ttu-id="2c943-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2c943-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2c943-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c943-112">Description</span></span>  
 <span data-ttu-id="2c943-113">Bir iş akışı uygulaması işlenmeyen bir özel durumla karşılaştı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c943-113">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2c943-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2c943-114">Message</span></span>  
 <span data-ttu-id="2c943-115">İş akışı örneği kimliği: '%1' işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="2c943-115">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="2c943-116">Özel durum '%2', DisplayName etkinliğinden kaynaklanan: '%3'.</span><span class="sxs-lookup"><span data-stu-id="2c943-116">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="2c943-117">Aşağıdaki işlem yapılmaz: %4.</span><span class="sxs-lookup"><span data-stu-id="2c943-117">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2c943-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2c943-118">Details</span></span>  
  
|<span data-ttu-id="2c943-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2c943-119">Data Item Name</span></span>|<span data-ttu-id="2c943-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2c943-120">Data Item Type</span></span>|<span data-ttu-id="2c943-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c943-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2c943-122">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="2c943-122">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="2c943-123">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="2c943-123">The instance id for the workflow</span></span>|  
|<span data-ttu-id="2c943-124">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="2c943-124">Exception</span></span>|`xs:string`|<span data-ttu-id="2c943-125">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="2c943-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="2c943-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2c943-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2c943-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2c943-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
