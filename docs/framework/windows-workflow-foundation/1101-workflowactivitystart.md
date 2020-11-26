---
title: 1101 - WorkflowActivityStart
ms.date: 03/30/2017
ms.assetid: 831cd386-b9b5-47a9-9690-aff6292ff348
ms.openlocfilehash: 6e43b0ab1e2d35657bae43e7239a677643154fa9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238736"
---
# <a name="1101---workflowactivitystart"></a><span data-ttu-id="a59f0-102">1101 - WorkflowActivityStart</span><span class="sxs-lookup"><span data-stu-id="a59f0-102">1101 - WorkflowActivityStart</span></span>

## <a name="properties"></a><span data-ttu-id="a59f0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a59f0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a59f0-104">ID</span><span class="sxs-lookup"><span data-stu-id="a59f0-104">ID</span></span>|<span data-ttu-id="a59f0-105">1101</span><span class="sxs-lookup"><span data-stu-id="a59f0-105">1101</span></span>|  
|<span data-ttu-id="a59f0-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a59f0-106">Keywords</span></span>|<span data-ttu-id="a59f0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a59f0-107">WFRuntime</span></span>|  
|<span data-ttu-id="a59f0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a59f0-108">Level</span></span>|<span data-ttu-id="a59f0-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="a59f0-109">Information</span></span>|  
|<span data-ttu-id="a59f0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a59f0-110">Channel</span></span>|<span data-ttu-id="a59f0-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="a59f0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a59f0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a59f0-112">Description</span></span>  

 <span data-ttu-id="a59f0-113">Bir iş akışı etkinliğinin başlatıldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a59f0-113">Indicates a workflow activity has started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a59f0-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a59f0-114">Message</span></span>  

 <span data-ttu-id="a59f0-115">WorkflowInstance kimliği: ' %1 ' E2E etkinliği</span><span class="sxs-lookup"><span data-stu-id="a59f0-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="a59f0-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a59f0-116">Details</span></span>  
  
|<span data-ttu-id="a59f0-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a59f0-117">Data Item Name</span></span>|<span data-ttu-id="a59f0-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a59f0-118">Data Item Type</span></span>|<span data-ttu-id="a59f0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a59f0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a59f0-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="a59f0-120">WorkflowInstanceId</span></span>|<span data-ttu-id="a59f0-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="a59f0-121">xs:string</span></span>|<span data-ttu-id="a59f0-122">İş akışı örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="a59f0-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="a59f0-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a59f0-123">AppDomain</span></span>|<span data-ttu-id="a59f0-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="a59f0-124">xs:string</span></span>|<span data-ttu-id="a59f0-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a59f0-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
