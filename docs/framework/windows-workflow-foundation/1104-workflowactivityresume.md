---
title: 1104 - WorkflowActivityResume
ms.date: 03/30/2017
ms.assetid: 7fe95d1e-34bd-43ca-b92e-587d2d248fff
ms.openlocfilehash: 2a9c40e2c403d43dc980af116e4b6e98b3b2090b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243566"
---
# <a name="1104---workflowactivityresume"></a><span data-ttu-id="5d929-102">1104 - WorkflowActivityResume</span><span class="sxs-lookup"><span data-stu-id="5d929-102">1104 - WorkflowActivityResume</span></span>

## <a name="properties"></a><span data-ttu-id="5d929-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5d929-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d929-104">ID</span><span class="sxs-lookup"><span data-stu-id="5d929-104">ID</span></span>|<span data-ttu-id="5d929-105">1104</span><span class="sxs-lookup"><span data-stu-id="5d929-105">1104</span></span>|  
|<span data-ttu-id="5d929-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="5d929-106">Keywords</span></span>|<span data-ttu-id="5d929-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5d929-107">WFRuntime</span></span>|  
|<span data-ttu-id="5d929-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="5d929-108">Level</span></span>|<span data-ttu-id="5d929-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="5d929-109">Information</span></span>|  
|<span data-ttu-id="5d929-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="5d929-110">Channel</span></span>|<span data-ttu-id="5d929-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="5d929-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5d929-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d929-112">Description</span></span>  

 <span data-ttu-id="5d929-113">Bir iş akışı etkinliğinin sürdürüldüğünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d929-113">Indicates a workflow activity has been resumed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5d929-114">İleti</span><span class="sxs-lookup"><span data-stu-id="5d929-114">Message</span></span>  

 <span data-ttu-id="5d929-115">WorkflowInstance kimliği: ' %1 ' E2E etkinliği</span><span class="sxs-lookup"><span data-stu-id="5d929-115">WorkflowInstance Id: '%1' E2E Activity</span></span>  
  
## <a name="details"></a><span data-ttu-id="5d929-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5d929-116">Details</span></span>  
  
|<span data-ttu-id="5d929-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="5d929-117">Data Item Name</span></span>|<span data-ttu-id="5d929-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="5d929-118">Data Item Type</span></span>|<span data-ttu-id="5d929-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5d929-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5d929-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="5d929-120">WorkflowInstanceId</span></span>|<span data-ttu-id="5d929-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="5d929-121">xs:string</span></span>|<span data-ttu-id="5d929-122">İş akışı örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="5d929-122">The workflow instance id.</span></span>|  
|<span data-ttu-id="5d929-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5d929-123">AppDomain</span></span>|<span data-ttu-id="5d929-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="5d929-124">xs:string</span></span>|<span data-ttu-id="5d929-125">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="5d929-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
