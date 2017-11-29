---
title: 1008 - WorkflowApplicationUnloaded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a605b780-4a7e-43ab-92e7-0a3b01d053b0
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 297b3ad9a677d28d12d1b00fdaeec8ec94842263
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1008---workflowapplicationunloaded"></a><span data-ttu-id="2b059-102">1008 - WorkflowApplicationUnloaded</span><span class="sxs-lookup"><span data-stu-id="2b059-102">1008 - WorkflowApplicationUnloaded</span></span>
## <a name="properties"></a><span data-ttu-id="2b059-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2b059-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b059-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="2b059-104">ID</span></span>|<span data-ttu-id="2b059-105">1008</span><span class="sxs-lookup"><span data-stu-id="2b059-105">1008</span></span>|  
|<span data-ttu-id="2b059-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="2b059-106">Keywords</span></span>|<span data-ttu-id="2b059-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2b059-107">WFRuntime</span></span>|  
|<span data-ttu-id="2b059-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2b059-108">Level</span></span>|<span data-ttu-id="2b059-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="2b059-109">Information</span></span>|  
|<span data-ttu-id="2b059-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2b059-110">Channel</span></span>|<span data-ttu-id="2b059-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2b059-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2b059-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b059-112">Description</span></span>  
 <span data-ttu-id="2b059-113">Bir iş akışı uygulaması kaldırıldı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b059-113">Indicates a workflow application has unloaded.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2b059-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2b059-114">Message</span></span>  
 <span data-ttu-id="2b059-115">İş akışı örneği kimliği: '%1'. yüklenmeyen.</span><span class="sxs-lookup"><span data-stu-id="2b059-115">WorkflowInstance Id: '%1' was Unloaded.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2b059-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2b059-116">Details</span></span>  
  
|<span data-ttu-id="2b059-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2b059-117">Data Item Name</span></span>|<span data-ttu-id="2b059-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2b059-118">Data Item Type</span></span>|<span data-ttu-id="2b059-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2b059-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2b059-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="2b059-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="2b059-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="2b059-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="2b059-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2b059-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2b059-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2b059-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
