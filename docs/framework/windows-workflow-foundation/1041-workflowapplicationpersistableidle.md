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
ms.openlocfilehash: b321f8c20fbd79b5e748601ee06f975dc75a7d56
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="184bf-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="184bf-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="184bf-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="184bf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="184bf-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="184bf-104">ID</span></span>|<span data-ttu-id="184bf-105">1041</span><span class="sxs-lookup"><span data-stu-id="184bf-105">1041</span></span>|  
|<span data-ttu-id="184bf-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="184bf-106">Keywords</span></span>|<span data-ttu-id="184bf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="184bf-107">WFRuntime</span></span>|  
|<span data-ttu-id="184bf-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="184bf-108">Level</span></span>|<span data-ttu-id="184bf-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="184bf-109">Information</span></span>|  
|<span data-ttu-id="184bf-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="184bf-110">Channel</span></span>|<span data-ttu-id="184bf-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="184bf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="184bf-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="184bf-112">Description</span></span>  
 <span data-ttu-id="184bf-113">Bir iş akışı uygulaması boşta ve kalıcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="184bf-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="184bf-114">İş akışı uygulama idled ya da kalıcı.</span><span class="sxs-lookup"><span data-stu-id="184bf-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="184bf-115">İleti</span><span class="sxs-lookup"><span data-stu-id="184bf-115">Message</span></span>  
 <span data-ttu-id="184bf-116">WorkflowApplication kimliği: boşta ve kalıcı '%1'.</span><span class="sxs-lookup"><span data-stu-id="184bf-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="184bf-117">Aşağıdaki işlem yapılmaz: %2.</span><span class="sxs-lookup"><span data-stu-id="184bf-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="184bf-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="184bf-118">Details</span></span>  
  
|<span data-ttu-id="184bf-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="184bf-119">Data Item Name</span></span>|<span data-ttu-id="184bf-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="184bf-120">Data Item Type</span></span>|<span data-ttu-id="184bf-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="184bf-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="184bf-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="184bf-122">WorkflowApplicationId</span></span>|<span data-ttu-id="184bf-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="184bf-123">xs:string</span></span>|<span data-ttu-id="184bf-124">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="184bf-124">The workflow application id</span></span>|  
|<span data-ttu-id="184bf-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="184bf-125">ActionTaken</span></span>|<span data-ttu-id="184bf-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="184bf-126">xs:string</span></span>|<span data-ttu-id="184bf-127">İş akışı uygulaması üzerinde gerçekleştirilecek eylem.</span><span class="sxs-lookup"><span data-stu-id="184bf-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="184bf-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="184bf-128">AppDomain</span></span>|<span data-ttu-id="184bf-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="184bf-129">xs:string</span></span>|<span data-ttu-id="184bf-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="184bf-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
