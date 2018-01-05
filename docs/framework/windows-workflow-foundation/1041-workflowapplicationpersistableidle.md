---
title: 1041 - WorkflowApplicationPersistableIdle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1efc32ed0304d5b0d222054e5c65abe279ef93ae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="fdfdd-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="fdfdd-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="fdfdd-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="fdfdd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fdfdd-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="fdfdd-104">ID</span></span>|<span data-ttu-id="fdfdd-105">1041</span><span class="sxs-lookup"><span data-stu-id="fdfdd-105">1041</span></span>|  
|<span data-ttu-id="fdfdd-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="fdfdd-106">Keywords</span></span>|<span data-ttu-id="fdfdd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="fdfdd-107">WFRuntime</span></span>|  
|<span data-ttu-id="fdfdd-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="fdfdd-108">Level</span></span>|<span data-ttu-id="fdfdd-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="fdfdd-109">Information</span></span>|  
|<span data-ttu-id="fdfdd-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="fdfdd-110">Channel</span></span>|<span data-ttu-id="fdfdd-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="fdfdd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fdfdd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdfdd-112">Description</span></span>  
 <span data-ttu-id="fdfdd-113">Bir iş akışı uygulaması boşta ve kalıcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="fdfdd-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="fdfdd-114">İş akışı uygulama idled ya da kalıcı.</span><span class="sxs-lookup"><span data-stu-id="fdfdd-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fdfdd-115">İleti</span><span class="sxs-lookup"><span data-stu-id="fdfdd-115">Message</span></span>  
 <span data-ttu-id="fdfdd-116">WorkflowApplication kimliği: boşta ve kalıcı '%1'.</span><span class="sxs-lookup"><span data-stu-id="fdfdd-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="fdfdd-117">Aşağıdaki işlem yapılmaz: %2.</span><span class="sxs-lookup"><span data-stu-id="fdfdd-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fdfdd-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fdfdd-118">Details</span></span>  
  
|<span data-ttu-id="fdfdd-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="fdfdd-119">Data Item Name</span></span>|<span data-ttu-id="fdfdd-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="fdfdd-120">Data Item Type</span></span>|<span data-ttu-id="fdfdd-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdfdd-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fdfdd-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="fdfdd-122">WorkflowApplicationId</span></span>|<span data-ttu-id="fdfdd-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="fdfdd-123">xs:string</span></span>|<span data-ttu-id="fdfdd-124">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="fdfdd-124">The workflow application id</span></span>|  
|<span data-ttu-id="fdfdd-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="fdfdd-125">ActionTaken</span></span>|<span data-ttu-id="fdfdd-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="fdfdd-126">xs:string</span></span>|<span data-ttu-id="fdfdd-127">İş akışı uygulaması üzerinde gerçekleştirilecek eylem.</span><span class="sxs-lookup"><span data-stu-id="fdfdd-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="fdfdd-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fdfdd-128">AppDomain</span></span>|<span data-ttu-id="fdfdd-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="fdfdd-129">xs:string</span></span>|<span data-ttu-id="fdfdd-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="fdfdd-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
