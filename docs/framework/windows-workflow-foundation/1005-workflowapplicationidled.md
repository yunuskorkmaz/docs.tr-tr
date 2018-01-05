---
title: 1005 - WorkflowApplicationIdled
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74d77dfa-f20d-4fe9-a6ae-e6d1b5fe4182
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dc9f8f72000fe283baa5bb2814e41051c1424983
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1005---workflowapplicationidled"></a><span data-ttu-id="1bd87-102">1005 - WorkflowApplicationIdled</span><span class="sxs-lookup"><span data-stu-id="1bd87-102">1005 - WorkflowApplicationIdled</span></span>
## <a name="properties"></a><span data-ttu-id="1bd87-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1bd87-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1bd87-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="1bd87-104">ID</span></span>|<span data-ttu-id="1bd87-105">1005</span><span class="sxs-lookup"><span data-stu-id="1bd87-105">1005</span></span>|  
|<span data-ttu-id="1bd87-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="1bd87-106">Keywords</span></span>|<span data-ttu-id="1bd87-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="1bd87-107">WFRuntime</span></span>|  
|<span data-ttu-id="1bd87-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1bd87-108">Level</span></span>|<span data-ttu-id="1bd87-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="1bd87-109">Information</span></span>|  
|<span data-ttu-id="1bd87-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1bd87-110">Channel</span></span>|<span data-ttu-id="1bd87-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="1bd87-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1bd87-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bd87-112">Description</span></span>  
 <span data-ttu-id="1bd87-113">Bir iş akışı uygulaması idled gösterir.</span><span class="sxs-lookup"><span data-stu-id="1bd87-113">Indicates a workflow application has idled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1bd87-114">İleti</span><span class="sxs-lookup"><span data-stu-id="1bd87-114">Message</span></span>  
 <span data-ttu-id="1bd87-115">WorkflowApplication kimliği: '%1' boşta geçti.</span><span class="sxs-lookup"><span data-stu-id="1bd87-115">WorkflowApplication Id: '%1' went idle.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1bd87-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1bd87-116">Details</span></span>  
  
|<span data-ttu-id="1bd87-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1bd87-117">Data Item Name</span></span>|<span data-ttu-id="1bd87-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1bd87-118">Data Item Type</span></span>|<span data-ttu-id="1bd87-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bd87-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1bd87-120">WorkflowInstanceID</span><span class="sxs-lookup"><span data-stu-id="1bd87-120">WorkflowInstanceId</span></span>|`xs:string`|<span data-ttu-id="1bd87-121">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="1bd87-121">The workflow application id</span></span>|  
|<span data-ttu-id="1bd87-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1bd87-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1bd87-123">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1bd87-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
