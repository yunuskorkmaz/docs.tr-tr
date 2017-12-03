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
ms.openlocfilehash: 0fcd6662c0f8899b6830dc8e06cee4f56b5ff906
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="8a1a0-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="8a1a0-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="8a1a0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8a1a0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8a1a0-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="8a1a0-104">ID</span></span>|<span data-ttu-id="8a1a0-105">1035</span><span class="sxs-lookup"><span data-stu-id="8a1a0-105">1035</span></span>|  
|<span data-ttu-id="8a1a0-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="8a1a0-106">Keywords</span></span>|<span data-ttu-id="8a1a0-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="8a1a0-107">WFRuntime</span></span>|  
|<span data-ttu-id="8a1a0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="8a1a0-108">Level</span></span>|<span data-ttu-id="8a1a0-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="8a1a0-109">Verbose</span></span>|  
|<span data-ttu-id="8a1a0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="8a1a0-110">Channel</span></span>|<span data-ttu-id="8a1a0-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="8a1a0-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8a1a0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a1a0-112">Description</span></span>  
 <span data-ttu-id="8a1a0-113">Etkinlik çalışma zamanı işlem ayarlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="8a1a0-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8a1a0-114">İleti</span><span class="sxs-lookup"><span data-stu-id="8a1a0-114">Message</span></span>  
 <span data-ttu-id="8a1a0-115">Çalışma zamanı işlem '%1', DisplayName etkinliği tarafından ayarlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="8a1a0-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="8a1a0-116">Etkinlik '%4', DisplayName yalıtılmış yürütme: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="8a1a0-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8a1a0-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8a1a0-117">Details</span></span>  
  
|<span data-ttu-id="8a1a0-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8a1a0-118">Data Item Name</span></span>|<span data-ttu-id="8a1a0-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8a1a0-119">Data Item Type</span></span>|<span data-ttu-id="8a1a0-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a1a0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8a1a0-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="8a1a0-121">Activity</span></span>|<span data-ttu-id="8a1a0-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="8a1a0-122">xs:string</span></span>|<span data-ttu-id="8a1a0-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="8a1a0-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="8a1a0-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="8a1a0-124">DisplayName</span></span>|<span data-ttu-id="8a1a0-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="8a1a0-125">xs:string</span></span>|<span data-ttu-id="8a1a0-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="8a1a0-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="8a1a0-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="8a1a0-127">InstanceId</span></span>|<span data-ttu-id="8a1a0-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="8a1a0-128">xs:string</span></span>|<span data-ttu-id="8a1a0-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="8a1a0-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="8a1a0-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="8a1a0-130">IsolatedActivity</span></span>|<span data-ttu-id="8a1a0-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="8a1a0-131">xs:string</span></span>|<span data-ttu-id="8a1a0-132">İşlem için yalıtılmış etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="8a1a0-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="8a1a0-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="8a1a0-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="8a1a0-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="8a1a0-134">xs:string</span></span>|<span data-ttu-id="8a1a0-135">İşlem için yalıtılmış etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="8a1a0-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="8a1a0-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="8a1a0-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="8a1a0-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="8a1a0-137">xs:string</span></span>|<span data-ttu-id="8a1a0-138">İşlem için yalıtılmış etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="8a1a0-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="8a1a0-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8a1a0-139">AppDomain</span></span>|<span data-ttu-id="8a1a0-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="8a1a0-140">xs:string</span></span>|<span data-ttu-id="8a1a0-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8a1a0-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
