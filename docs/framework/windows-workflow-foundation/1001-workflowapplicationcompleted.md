---
title: 1001 - WorkflowApplicationCompleted
ms.date: 03/30/2017
ms.assetid: 7a2ab59a-cf66-437a-b01e-f8f7268a3f7a
ms.openlocfilehash: be97991be9b61908a23486da0ef255ebfbdc5485
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239958"
---
# <a name="1001---workflowapplicationcompleted"></a><span data-ttu-id="e2bac-102">1001 - WorkflowApplicationCompleted</span><span class="sxs-lookup"><span data-stu-id="e2bac-102">1001 - WorkflowApplicationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="e2bac-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e2bac-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e2bac-104">ID</span><span class="sxs-lookup"><span data-stu-id="e2bac-104">ID</span></span>|<span data-ttu-id="e2bac-105">1001</span><span class="sxs-lookup"><span data-stu-id="e2bac-105">1001</span></span>|  
|<span data-ttu-id="e2bac-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e2bac-106">Keywords</span></span>|<span data-ttu-id="e2bac-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="e2bac-107">WFRuntime</span></span>|  
|<span data-ttu-id="e2bac-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e2bac-108">Level</span></span>|<span data-ttu-id="e2bac-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="e2bac-109">Information</span></span>|  
|<span data-ttu-id="e2bac-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e2bac-110">Channel</span></span>|<span data-ttu-id="e2bac-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="e2bac-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e2bac-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2bac-112">Description</span></span>  

 <span data-ttu-id="e2bac-113">Bir iş akışı uygulamasının kapalı durumda tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2bac-113">Indicates a workflow application has completed in the Closed state.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e2bac-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e2bac-114">Message</span></span>  

 <span data-ttu-id="e2bac-115">WorkflowInstance kimliği: ' %1 ' kapalı durumda tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="e2bac-115">WorkflowInstance Id: '%1' has completed in the Closed state.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e2bac-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e2bac-116">Details</span></span>  
  
|<span data-ttu-id="e2bac-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e2bac-117">Data Item Name</span></span>|<span data-ttu-id="e2bac-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e2bac-118">Data Item Type</span></span>|<span data-ttu-id="e2bac-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e2bac-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e2bac-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="e2bac-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="e2bac-121">İş akışının örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="e2bac-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="e2bac-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e2bac-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e2bac-123">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e2bac-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
