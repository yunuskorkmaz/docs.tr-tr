---
description: 'Hakkında daha fazla bilgi edinin: 1041-Workflowapplicationpersistableıdle'
title: 1041 - WorkflowApplicationPersistableIdle
ms.date: 03/30/2017
ms.assetid: 966adf2f-e21d-44df-a3ec-a8e285e0a316
ms.openlocfilehash: eb004077a36ed3e78229df92a73972ed5feda665
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667765"
---
# <a name="1041---workflowapplicationpersistableidle"></a><span data-ttu-id="8d131-103">1041 - WorkflowApplicationPersistableIdle</span><span class="sxs-lookup"><span data-stu-id="8d131-103">1041 - WorkflowApplicationPersistableIdle</span></span>

## <a name="properties"></a><span data-ttu-id="8d131-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8d131-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8d131-105">ID</span><span class="sxs-lookup"><span data-stu-id="8d131-105">ID</span></span>|<span data-ttu-id="8d131-106">1041</span><span class="sxs-lookup"><span data-stu-id="8d131-106">1041</span></span>|  
|<span data-ttu-id="8d131-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="8d131-107">Keywords</span></span>|<span data-ttu-id="8d131-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8d131-108">WFRuntime</span></span>|  
|<span data-ttu-id="8d131-109">Level</span><span class="sxs-lookup"><span data-stu-id="8d131-109">Level</span></span>|<span data-ttu-id="8d131-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="8d131-110">Information</span></span>|  
|<span data-ttu-id="8d131-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="8d131-111">Channel</span></span>|<span data-ttu-id="8d131-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="8d131-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8d131-113">Description</span><span class="sxs-lookup"><span data-stu-id="8d131-113">Description</span></span>  

 <span data-ttu-id="8d131-114">Bir iş akışı uygulamasının boşta ve kalıcı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d131-114">Indicates that a workflow application is idle and persistable.</span></span> <span data-ttu-id="8d131-115">İş akışı uygulaması bırakılacak veya kalıcı olacak.</span><span class="sxs-lookup"><span data-stu-id="8d131-115">The workflow application will be idled or persisted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8d131-116">İleti</span><span class="sxs-lookup"><span data-stu-id="8d131-116">Message</span></span>  

 <span data-ttu-id="8d131-117">WorkflowApplication kimliği: ' %1 ' boşta ve sürekli tablo.</span><span class="sxs-lookup"><span data-stu-id="8d131-117">WorkflowApplication Id: '%1' is idle and persistable.</span></span>  <span data-ttu-id="8d131-118">Şu işlem gerçekleştirilecek: %2.</span><span class="sxs-lookup"><span data-stu-id="8d131-118">The following action will be taken: %2.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8d131-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8d131-119">Details</span></span>  
  
|<span data-ttu-id="8d131-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8d131-120">Data Item Name</span></span>|<span data-ttu-id="8d131-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8d131-121">Data Item Type</span></span>|<span data-ttu-id="8d131-122">Description</span><span class="sxs-lookup"><span data-stu-id="8d131-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8d131-123">Workflowapplicationıd</span><span class="sxs-lookup"><span data-stu-id="8d131-123">WorkflowApplicationId</span></span>|<span data-ttu-id="8d131-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="8d131-124">xs:string</span></span>|<span data-ttu-id="8d131-125">İş akışı uygulama kimliği</span><span class="sxs-lookup"><span data-stu-id="8d131-125">The workflow application id</span></span>|  
|<span data-ttu-id="8d131-126">Gerçekleştirilen eylem</span><span class="sxs-lookup"><span data-stu-id="8d131-126">ActionTaken</span></span>|<span data-ttu-id="8d131-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="8d131-127">xs:string</span></span>|<span data-ttu-id="8d131-128">İş akışı uygulamasında gerçekleştirilecek eylem.</span><span class="sxs-lookup"><span data-stu-id="8d131-128">The action that will be taken on the workflow application.</span></span>|  
|<span data-ttu-id="8d131-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8d131-129">AppDomain</span></span>|<span data-ttu-id="8d131-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="8d131-130">xs:string</span></span>|<span data-ttu-id="8d131-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8d131-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
