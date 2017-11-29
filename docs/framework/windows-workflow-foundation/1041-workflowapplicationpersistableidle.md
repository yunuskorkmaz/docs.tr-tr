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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ea6b31a83df6e15fe34f9e4be31a4eb53bc5bb51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="110b9-102">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="110b9-102">1041 - WorkflowApplicationPersistableIdle</span></span>
## <a name="properties"></a><span data-ttu-id="110b9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="110b9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="110b9-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="110b9-104">ID</span></span>|<span data-ttu-id="110b9-105">1041</span><span class="sxs-lookup"><span data-stu-id="110b9-105">1041</span></span>|  
|<span data-ttu-id="110b9-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="110b9-106">Keywords</span></span>|<span data-ttu-id="110b9-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="110b9-107">WFRuntime</span></span>|  
|<span data-ttu-id="110b9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="110b9-108">Level</span></span>|<span data-ttu-id="110b9-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="110b9-109">Information</span></span>|  
|<span data-ttu-id="110b9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="110b9-110">Channel</span></span>|<span data-ttu-id="110b9-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="110b9-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="110b9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="110b9-112">Description</span></span>  
 <span data-ttu-id="110b9-113">Bir iş akışı uygulaması boşta ve kalıcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="110b9-113">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="110b9-114">İş akışı uygulama idled ya da kalıcı.</span><span class="sxs-lookup"><span data-stu-id="110b9-114">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="110b9-115">İleti</span><span class="sxs-lookup"><span data-stu-id="110b9-115">Message</span></span>  
 <span data-ttu-id="110b9-116">WorkflowApplication kimliği: boşta ve kalıcı '%1'.</span><span class="sxs-lookup"><span data-stu-id="110b9-116">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="110b9-117">Aşağıdaki işlem yapılmaz: %2.</span><span class="sxs-lookup"><span data-stu-id="110b9-117">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="110b9-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="110b9-118">Details</span></span>  
  
|<span data-ttu-id="110b9-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="110b9-119">Data Item Name</span></span>|<span data-ttu-id="110b9-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="110b9-120">Data Item Type</span></span>|<span data-ttu-id="110b9-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="110b9-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="110b9-122">WorkflowApplicationId</span><span class="sxs-lookup"><span data-stu-id="110b9-122">WorkflowApplicationId</span></span>|<span data-ttu-id="110b9-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="110b9-123">xs:string</span></span>|<span data-ttu-id="110b9-124">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="110b9-124">The workflow application id</span></span>|  
|<span data-ttu-id="110b9-125">ActionTaken</span><span class="sxs-lookup"><span data-stu-id="110b9-125">ActionTaken</span></span>|<span data-ttu-id="110b9-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="110b9-126">xs:string</span></span>|<span data-ttu-id="110b9-127">İş akışı uygulaması üzerinde gerçekleştirilecek eylem.</span><span class="sxs-lookup"><span data-stu-id="110b9-127">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="110b9-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="110b9-128">AppDomain</span></span>|<span data-ttu-id="110b9-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="110b9-129">xs:string</span></span>|<span data-ttu-id="110b9-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="110b9-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
