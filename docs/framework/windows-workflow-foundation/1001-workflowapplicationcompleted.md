---
description: 'Hakkında daha fazla bilgi edinin: 1001-WorkflowApplicationCompleted'
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: d32028bbe582f4a1e31796ed1f75e41c651e6c59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755648"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="81aa6-103">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="81aa6-103">1001 - WorkflowApplicationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="81aa6-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="81aa6-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="81aa6-105">ID</span><span class="sxs-lookup"><span data-stu-id="81aa6-105">ID</span></span>|<span data-ttu-id="81aa6-106">1001</span><span class="sxs-lookup"><span data-stu-id="81aa6-106">1001</span></span>|  
|<span data-ttu-id="81aa6-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="81aa6-107">Keywords</span></span>|<span data-ttu-id="81aa6-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="81aa6-108">WFRuntime</span></span>|  
|<span data-ttu-id="81aa6-109">Level</span><span class="sxs-lookup"><span data-stu-id="81aa6-109">Level</span></span>|<span data-ttu-id="81aa6-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="81aa6-110">Information</span></span>|  
|<span data-ttu-id="81aa6-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="81aa6-111">Channel</span></span>|<span data-ttu-id="81aa6-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="81aa6-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="81aa6-113">Description</span><span class="sxs-lookup"><span data-stu-id="81aa6-113">Description</span></span>  

 <span data-ttu-id="81aa6-114">Bir iş akışı uygulamasının kapalı durumda tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="81aa6-114">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="81aa6-115">İleti</span><span class="sxs-lookup"><span data-stu-id="81aa6-115">Message</span></span>  

 <span data-ttu-id="81aa6-116">WorkflowInstance kimliği: ' %1 ' kapalı durumda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="81aa6-116">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="81aa6-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="81aa6-117">Details</span></span>  
  
|<span data-ttu-id="81aa6-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="81aa6-118">Data Item Name</span></span>|<span data-ttu-id="81aa6-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="81aa6-119">Data Item Type</span></span>|<span data-ttu-id="81aa6-120">Description</span><span class="sxs-lookup"><span data-stu-id="81aa6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="81aa6-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="81aa6-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="81aa6-122">İş akışının örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="81aa6-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="81aa6-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="81aa6-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="81aa6-124">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="81aa6-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
