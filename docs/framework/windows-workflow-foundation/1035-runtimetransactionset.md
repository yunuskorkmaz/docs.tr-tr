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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c3fcd93dbc30b20f7822a54babde8277e32d8335
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="71a08-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="71a08-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="71a08-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="71a08-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71a08-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="71a08-104">ID</span></span>|<span data-ttu-id="71a08-105">1035</span><span class="sxs-lookup"><span data-stu-id="71a08-105">1035</span></span>|  
|<span data-ttu-id="71a08-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="71a08-106">Keywords</span></span>|<span data-ttu-id="71a08-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="71a08-107">WFRuntime</span></span>|  
|<span data-ttu-id="71a08-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="71a08-108">Level</span></span>|<span data-ttu-id="71a08-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="71a08-109">Verbose</span></span>|  
|<span data-ttu-id="71a08-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="71a08-110">Channel</span></span>|<span data-ttu-id="71a08-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="71a08-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="71a08-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71a08-112">Description</span></span>  
 <span data-ttu-id="71a08-113">Etkinlik çalışma zamanı işlem ayarlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="71a08-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="71a08-114">İleti</span><span class="sxs-lookup"><span data-stu-id="71a08-114">Message</span></span>  
 <span data-ttu-id="71a08-115">Çalışma zamanı işlem '%1', DisplayName etkinliği tarafından ayarlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="71a08-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="71a08-116">Etkinlik '%4', DisplayName yalıtılmış yürütme: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="71a08-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="71a08-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="71a08-117">Details</span></span>  
  
|<span data-ttu-id="71a08-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="71a08-118">Data Item Name</span></span>|<span data-ttu-id="71a08-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="71a08-119">Data Item Type</span></span>|<span data-ttu-id="71a08-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71a08-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="71a08-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="71a08-121">Activity</span></span>|<span data-ttu-id="71a08-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="71a08-122">xs:string</span></span>|<span data-ttu-id="71a08-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="71a08-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="71a08-124">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="71a08-124">DisplayName</span></span>|<span data-ttu-id="71a08-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="71a08-125">xs:string</span></span>|<span data-ttu-id="71a08-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="71a08-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="71a08-127">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="71a08-127">InstanceId</span></span>|<span data-ttu-id="71a08-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="71a08-128">xs:string</span></span>|<span data-ttu-id="71a08-129">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="71a08-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="71a08-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="71a08-130">IsolatedActivity</span></span>|<span data-ttu-id="71a08-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="71a08-131">xs:string</span></span>|<span data-ttu-id="71a08-132">İşlem için yalıtılmış etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="71a08-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="71a08-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="71a08-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="71a08-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="71a08-134">xs:string</span></span>|<span data-ttu-id="71a08-135">İşlem için yalıtılmış etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="71a08-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="71a08-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="71a08-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="71a08-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="71a08-137">xs:string</span></span>|<span data-ttu-id="71a08-138">İşlem için yalıtılmış etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="71a08-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="71a08-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="71a08-139">AppDomain</span></span>|<span data-ttu-id="71a08-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="71a08-140">xs:string</span></span>|<span data-ttu-id="71a08-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="71a08-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
