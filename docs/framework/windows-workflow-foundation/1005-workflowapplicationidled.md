---
title: 1005 - WorkflowApplicationIdled
ms.date: 03/30/2017
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
ms.openlocfilehash: 3b7210246b7fb754145c8aa6128da3183cea9f91
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239867"
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="2ffb7-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="2ffb7-102">1005 - WorkflowApplicationIdled</span></span>

## <a name="properties"></a><span data-ttu-id="2ffb7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2ffb7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2ffb7-104">ID</span><span class="sxs-lookup"><span data-stu-id="2ffb7-104">ID</span></span>|<span data-ttu-id="2ffb7-105">1005</span><span class="sxs-lookup"><span data-stu-id="2ffb7-105">1005</span></span>|  
|<span data-ttu-id="2ffb7-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="2ffb7-106">Keywords</span></span>|<span data-ttu-id="2ffb7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2ffb7-107">WFRuntime</span></span>|  
|<span data-ttu-id="2ffb7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2ffb7-108">Level</span></span>|<span data-ttu-id="2ffb7-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="2ffb7-109">Information</span></span>|  
|<span data-ttu-id="2ffb7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2ffb7-110">Channel</span></span>|<span data-ttu-id="2ffb7-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="2ffb7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2ffb7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ffb7-112">Description</span></span>  

 <span data-ttu-id="2ffb7-113">Bir iş akışı uygulamasının ıdlenmiş olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ffb7-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2ffb7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2ffb7-114">Message</span></span>  

 <span data-ttu-id="2ffb7-115">WorkflowApplication kimliği: ' %1 ' boşta oldu.</span><span class="sxs-lookup"><span data-stu-id="2ffb7-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2ffb7-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2ffb7-116">Details</span></span>  
  
|<span data-ttu-id="2ffb7-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2ffb7-117">Data Item Name</span></span>|<span data-ttu-id="2ffb7-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2ffb7-118">Data Item Type</span></span>|<span data-ttu-id="2ffb7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ffb7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2ffb7-120">WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="2ffb7-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="2ffb7-121">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="2ffb7-121">The workflow application id</span></span>|  
|<span data-ttu-id="2ffb7-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2ffb7-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2ffb7-123">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2ffb7-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
