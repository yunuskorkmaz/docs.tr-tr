---
title: 1004 - WorkflowInstanceAborted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edb9ab8c-0b9a-488d-aa96-9c8c7984b53c
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7394ebbcb14850af89d906b0b573c4f677346825
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="f3d0b-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="f3d0b-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="f3d0b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f3d0b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3d0b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f3d0b-104">ID</span></span>|<span data-ttu-id="f3d0b-105">1004</span><span class="sxs-lookup"><span data-stu-id="f3d0b-105">1004</span></span>|  
|<span data-ttu-id="f3d0b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f3d0b-106">Keywords</span></span>|<span data-ttu-id="f3d0b-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="f3d0b-107">WFRuntime</span></span>|  
|<span data-ttu-id="f3d0b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f3d0b-108">Level</span></span>|<span data-ttu-id="f3d0b-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f3d0b-109">Information</span></span>|  
|<span data-ttu-id="f3d0b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f3d0b-110">Channel</span></span>|<span data-ttu-id="f3d0b-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="f3d0b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f3d0b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3d0b-112">Description</span></span>  
 <span data-ttu-id="f3d0b-113">Bir özel durum ile bir akışı örneği durdurdu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3d0b-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f3d0b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f3d0b-114">Message</span></span>  
 <span data-ttu-id="f3d0b-115">İş akışı örneği kimliği: '%1' olan bir özel durum durduruldu.</span><span class="sxs-lookup"><span data-stu-id="f3d0b-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f3d0b-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f3d0b-116">Details</span></span>  
  
|<span data-ttu-id="f3d0b-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f3d0b-117">Data Item Name</span></span>|<span data-ttu-id="f3d0b-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f3d0b-118">Data Item Type</span></span>|<span data-ttu-id="f3d0b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f3d0b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f3d0b-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="f3d0b-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="f3d0b-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="f3d0b-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="f3d0b-122">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="f3d0b-122">Exception</span></span>|`xs:string`|<span data-ttu-id="f3d0b-123">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="f3d0b-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="f3d0b-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f3d0b-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f3d0b-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f3d0b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
