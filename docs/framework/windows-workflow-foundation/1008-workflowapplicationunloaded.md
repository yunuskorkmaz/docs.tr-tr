---
description: 'Hakkında daha fazla bilgi edinin: 1008-Workflowapplicationyüklenmeyen'
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: 5e906c0daae525accc3b8b13c907479d18f2fc8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755570"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="0d8db-103">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="0d8db-103">1008 - WorkflowApplicationUnloaded</span></span>

## <a name="properties"></a><span data-ttu-id="0d8db-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0d8db-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0d8db-105">ID</span><span class="sxs-lookup"><span data-stu-id="0d8db-105">ID</span></span>|<span data-ttu-id="0d8db-106">1008</span><span class="sxs-lookup"><span data-stu-id="0d8db-106">1008</span></span>|  
|<span data-ttu-id="0d8db-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="0d8db-107">Keywords</span></span>|<span data-ttu-id="0d8db-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="0d8db-108">WFRuntime</span></span>|  
|<span data-ttu-id="0d8db-109">Level</span><span class="sxs-lookup"><span data-stu-id="0d8db-109">Level</span></span>|<span data-ttu-id="0d8db-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="0d8db-110">Information</span></span>|  
|<span data-ttu-id="0d8db-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="0d8db-111">Channel</span></span>|<span data-ttu-id="0d8db-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="0d8db-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0d8db-113">Description</span><span class="sxs-lookup"><span data-stu-id="0d8db-113">Description</span></span>  

 <span data-ttu-id="0d8db-114">Bir iş akışı uygulamasının bellekten kaldırılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0d8db-114">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0d8db-115">İleti</span><span class="sxs-lookup"><span data-stu-id="0d8db-115">Message</span></span>  

 <span data-ttu-id="0d8db-116">WorkflowInstance kimliği: ' %1 ' kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="0d8db-116">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0d8db-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0d8db-117">Details</span></span>  
  
|<span data-ttu-id="0d8db-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="0d8db-118">Data Item Name</span></span>|<span data-ttu-id="0d8db-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="0d8db-119">Data Item Type</span></span>|<span data-ttu-id="0d8db-120">Description</span><span class="sxs-lookup"><span data-stu-id="0d8db-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0d8db-121">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="0d8db-121">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="0d8db-122">İş akışının örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="0d8db-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="0d8db-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0d8db-123">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0d8db-124">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0d8db-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
