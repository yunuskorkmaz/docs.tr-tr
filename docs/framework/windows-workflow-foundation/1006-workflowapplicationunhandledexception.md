---
description: 'Hakkında daha fazla bilgi edinin: 1006-WorkflowApplicationUnhandledException'
title: 1006 - WorkflowApplicationUnhandledException
ms.date: 03/30/2017
ms.assetid: dfe0f316-e03b-47fb-b6a3-622c56bfd753
ms.openlocfilehash: bfccd0d12c5dac4caad1e84e95f1cd096a551aa0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755596"
---
# <a name="1006---workflowapplicationunhandledexception"></a><span data-ttu-id="4c616-103">1006 - WorkflowApplicationUnhandledException</span><span class="sxs-lookup"><span data-stu-id="4c616-103">1006 - WorkflowApplicationUnhandledException</span></span>

## <a name="properties"></a><span data-ttu-id="4c616-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4c616-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4c616-105">ID</span><span class="sxs-lookup"><span data-stu-id="4c616-105">ID</span></span>|<span data-ttu-id="4c616-106">1006</span><span class="sxs-lookup"><span data-stu-id="4c616-106">1006</span></span>|  
|<span data-ttu-id="4c616-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4c616-107">Keywords</span></span>|<span data-ttu-id="4c616-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4c616-108">WFRuntime</span></span>|  
|<span data-ttu-id="4c616-109">Level</span><span class="sxs-lookup"><span data-stu-id="4c616-109">Level</span></span>|<span data-ttu-id="4c616-110">Hata</span><span class="sxs-lookup"><span data-stu-id="4c616-110">Error</span></span>|  
|<span data-ttu-id="4c616-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="4c616-111">Channel</span></span>|<span data-ttu-id="4c616-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="4c616-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4c616-113">Description</span><span class="sxs-lookup"><span data-stu-id="4c616-113">Description</span></span>  

 <span data-ttu-id="4c616-114">Bir iş akışı uygulamasının işlenmemiş bir özel durumla karşılaşdığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4c616-114">Indicates a workflow application has encountered an unhandled exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4c616-115">İleti</span><span class="sxs-lookup"><span data-stu-id="4c616-115">Message</span></span>  

 <span data-ttu-id="4c616-116">WorkflowInstance kimliği: ' %1 ' işlenmeyen bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="4c616-116">WorkflowInstance Id: '%1' has encountered an unhandled exception.</span></span>  <span data-ttu-id="4c616-117">DisplayName: ' %3 ' olan ' %2 ' etkinliğinden kaynaklanan özel durum.</span><span class="sxs-lookup"><span data-stu-id="4c616-117">The exception originated from Activity '%2', DisplayName: '%3'.</span></span>  <span data-ttu-id="4c616-118">Şu işlem gerçekleştirilecek: %4.</span><span class="sxs-lookup"><span data-stu-id="4c616-118">The following action will be taken: %4.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4c616-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4c616-119">Details</span></span>  
  
|<span data-ttu-id="4c616-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4c616-120">Data Item Name</span></span>|<span data-ttu-id="4c616-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4c616-121">Data Item Type</span></span>|<span data-ttu-id="4c616-122">Description</span><span class="sxs-lookup"><span data-stu-id="4c616-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4c616-123">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="4c616-123">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="4c616-124">İş akışının örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="4c616-124">The instance id for the workflow</span></span>|  
|<span data-ttu-id="4c616-125">Özel durum</span><span class="sxs-lookup"><span data-stu-id="4c616-125">Exception</span></span>|`xs:string`|<span data-ttu-id="4c616-126">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="4c616-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="4c616-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4c616-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4c616-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4c616-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
