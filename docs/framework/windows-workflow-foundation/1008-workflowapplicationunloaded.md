---
title: 1008 - WorkflowApplicationUnloaded
ms.date: 03/30/2017
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
ms.openlocfilehash: 6ea121e7901d877d4f0d8f9f5bfd259c2f93696d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239837"
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="08c58-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="08c58-102">1008 - WorkflowApplicationUnloaded</span></span>

## <a name="properties"></a><span data-ttu-id="08c58-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="08c58-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08c58-104">ID</span><span class="sxs-lookup"><span data-stu-id="08c58-104">ID</span></span>|<span data-ttu-id="08c58-105">1008</span><span class="sxs-lookup"><span data-stu-id="08c58-105">1008</span></span>|  
|<span data-ttu-id="08c58-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="08c58-106">Keywords</span></span>|<span data-ttu-id="08c58-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="08c58-107">WFRuntime</span></span>|  
|<span data-ttu-id="08c58-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="08c58-108">Level</span></span>|<span data-ttu-id="08c58-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="08c58-109">Information</span></span>|  
|<span data-ttu-id="08c58-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="08c58-110">Channel</span></span>|<span data-ttu-id="08c58-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="08c58-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="08c58-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08c58-112">Description</span></span>  

 <span data-ttu-id="08c58-113">Bir iş akışı uygulamasının bellekten kaldırılmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="08c58-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="08c58-114">İleti</span><span class="sxs-lookup"><span data-stu-id="08c58-114">Message</span></span>  

 <span data-ttu-id="08c58-115">WorkflowInstance kimliği: ' %1 ' kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="08c58-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="08c58-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="08c58-116">Details</span></span>  
  
|<span data-ttu-id="08c58-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="08c58-117">Data Item Name</span></span>|<span data-ttu-id="08c58-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="08c58-118">Data Item Type</span></span>|<span data-ttu-id="08c58-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08c58-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="08c58-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="08c58-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="08c58-121">İş akışının örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="08c58-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="08c58-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="08c58-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="08c58-123">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="08c58-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
