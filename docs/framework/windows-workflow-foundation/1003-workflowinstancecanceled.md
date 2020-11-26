---
title: 1003 - WorkflowInstanceCanceled
ms.date: 03/30/2017
ms.assetid: 64754dc2-c160-4bf3-869a-13d56694e2dc
ms.openlocfilehash: bd8abf173ab6588d4a35ba59c6cd14fb53445e9f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239906"
---
# <a name="1003---workflowinstancecanceled"></a><span data-ttu-id="931e9-102">1003 - WorkflowInstanceCanceled</span><span class="sxs-lookup"><span data-stu-id="931e9-102">1003 - WorkflowInstanceCanceled</span></span>

## <a name="properties"></a><span data-ttu-id="931e9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="931e9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="931e9-104">ID</span><span class="sxs-lookup"><span data-stu-id="931e9-104">ID</span></span>|<span data-ttu-id="931e9-105">1003</span><span class="sxs-lookup"><span data-stu-id="931e9-105">1003</span></span>|  
|<span data-ttu-id="931e9-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="931e9-106">Keywords</span></span>|<span data-ttu-id="931e9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="931e9-107">WFRuntime</span></span>|  
|<span data-ttu-id="931e9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="931e9-108">Level</span></span>|<span data-ttu-id="931e9-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="931e9-109">Information</span></span>|  
|<span data-ttu-id="931e9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="931e9-110">Channel</span></span>|<span data-ttu-id="931e9-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="931e9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="931e9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="931e9-112">Description</span></span>  

 <span data-ttu-id="931e9-113">Iptal edilen durumda bir iş akışı örneğinin tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="931e9-113">Indicates a workflow instance has completed in the Canceled state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="931e9-114">İleti</span><span class="sxs-lookup"><span data-stu-id="931e9-114">Message</span></span>  

 <span data-ttu-id="931e9-115">WorkflowInstance kimliği: ' %1 ' Iptal edildi durumunda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="931e9-115">WorkflowInstance Id: '%1' has completed in the Canceled state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="931e9-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="931e9-116">Details</span></span>  
  
|<span data-ttu-id="931e9-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="931e9-117">Data Item Name</span></span>|<span data-ttu-id="931e9-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="931e9-118">Data Item Type</span></span>|<span data-ttu-id="931e9-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="931e9-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="931e9-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="931e9-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="931e9-121">İş akışının örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="931e9-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="931e9-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="931e9-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="931e9-123">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="931e9-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
