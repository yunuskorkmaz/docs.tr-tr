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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc940e1781f821f12efb42c5198e77eb0451a164
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1004---workflowinstanceaborted"></a><span data-ttu-id="1ec43-102">1004 - WorkflowInstanceAborted</span><span class="sxs-lookup"><span data-stu-id="1ec43-102">1004 - WorkflowInstanceAborted</span></span>
## <a name="properties"></a><span data-ttu-id="1ec43-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1ec43-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1ec43-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="1ec43-104">ID</span></span>|<span data-ttu-id="1ec43-105">1004</span><span class="sxs-lookup"><span data-stu-id="1ec43-105">1004</span></span>|  
|<span data-ttu-id="1ec43-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="1ec43-106">Keywords</span></span>|<span data-ttu-id="1ec43-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1ec43-107">WFRuntime</span></span>|  
|<span data-ttu-id="1ec43-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1ec43-108">Level</span></span>|<span data-ttu-id="1ec43-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="1ec43-109">Information</span></span>|  
|<span data-ttu-id="1ec43-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1ec43-110">Channel</span></span>|<span data-ttu-id="1ec43-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1ec43-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1ec43-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ec43-112">Description</span></span>  
 <span data-ttu-id="1ec43-113">Bir özel durum ile bir akışı örneği durdurdu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ec43-113">Indicates a worfklow instance has aborted with an exception.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1ec43-114">İleti</span><span class="sxs-lookup"><span data-stu-id="1ec43-114">Message</span></span>  
 <span data-ttu-id="1ec43-115">İş akışı örneği kimliği: '%1' olan bir özel durum durduruldu.</span><span class="sxs-lookup"><span data-stu-id="1ec43-115">WorkflowInstance Id: '%1' was aborted with an exception.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1ec43-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1ec43-116">Details</span></span>  
  
|<span data-ttu-id="1ec43-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1ec43-117">Data Item Name</span></span>|<span data-ttu-id="1ec43-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1ec43-118">Data Item Type</span></span>|<span data-ttu-id="1ec43-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ec43-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1ec43-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="1ec43-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="1ec43-121">İş akışı için örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="1ec43-121">The instance id for the workflow</span></span>|  
|<span data-ttu-id="1ec43-122">Özel Durum</span><span class="sxs-lookup"><span data-stu-id="1ec43-122">Exception</span></span>|`xs:string`|<span data-ttu-id="1ec43-123">Özel durum için özel durum ayrıntıları</span><span class="sxs-lookup"><span data-stu-id="1ec43-123">The exception details for the exception</span></span>|  
|<span data-ttu-id="1ec43-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1ec43-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1ec43-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1ec43-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
