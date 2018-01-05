---
title: 1035 - RuntimeTransactionSet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a64a8a4ab6212a5e83b59fd7523df9cd875e7b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="5733e-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="5733e-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="5733e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5733e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5733e-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="5733e-104">ID</span></span>|<span data-ttu-id="5733e-105">1035</span><span class="sxs-lookup"><span data-stu-id="5733e-105">1035</span></span>|  
|<span data-ttu-id="5733e-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="5733e-106">Keywords</span></span>|<span data-ttu-id="5733e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="5733e-107">WFRuntime</span></span>|  
|<span data-ttu-id="5733e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="5733e-108">Level</span></span>|<span data-ttu-id="5733e-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="5733e-109">Verbose</span></span>|  
|<span data-ttu-id="5733e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="5733e-110">Channel</span></span>|<span data-ttu-id="5733e-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="5733e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5733e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5733e-112">Description</span></span>  
 <span data-ttu-id="5733e-113">Etkinlik çalışma zamanı işlem ayarlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="5733e-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5733e-114">İleti</span><span class="sxs-lookup"><span data-stu-id="5733e-114">Message</span></span>  
 <span data-ttu-id="5733e-115">Çalışma zamanı işlem '%1', DisplayName etkinliği tarafından ayarlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="5733e-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="5733e-116">Etkinlik '%4', DisplayName yalıtılmış yürütme: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="5733e-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5733e-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5733e-117">Details</span></span>  
  
|<span data-ttu-id="5733e-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="5733e-118">Data Item Name</span></span>|<span data-ttu-id="5733e-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="5733e-119">Data Item Type</span></span>|<span data-ttu-id="5733e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5733e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5733e-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="5733e-121">Activity</span></span>|<span data-ttu-id="5733e-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="5733e-122">xs:string</span></span>|<span data-ttu-id="5733e-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="5733e-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="5733e-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="5733e-124">DisplayName</span></span>|<span data-ttu-id="5733e-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="5733e-125">xs:string</span></span>|<span data-ttu-id="5733e-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="5733e-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="5733e-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="5733e-127">InstanceId</span></span>|<span data-ttu-id="5733e-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="5733e-128">xs:string</span></span>|<span data-ttu-id="5733e-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="5733e-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="5733e-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="5733e-130">IsolatedActivity</span></span>|<span data-ttu-id="5733e-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="5733e-131">xs:string</span></span>|<span data-ttu-id="5733e-132">İşlem için yalıtılmış etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="5733e-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="5733e-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="5733e-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="5733e-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="5733e-134">xs:string</span></span>|<span data-ttu-id="5733e-135">İşlem için yalıtılmış etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="5733e-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="5733e-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="5733e-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="5733e-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="5733e-137">xs:string</span></span>|<span data-ttu-id="5733e-138">İşlem için yalıtılmış etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="5733e-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="5733e-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5733e-139">AppDomain</span></span>|<span data-ttu-id="5733e-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="5733e-140">xs:string</span></span>|<span data-ttu-id="5733e-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="5733e-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
