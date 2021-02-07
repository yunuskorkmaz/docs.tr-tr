---
description: 'Hakkında daha fazla bilgi edinin: 1035-RuntimeTransactionSet'
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 513ba49962a8f02ab47b8e5b762949cd09154a3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667908"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="599e6-103">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="599e6-103">1035 - RuntimeTransactionSet</span></span>

## <a name="properties"></a><span data-ttu-id="599e6-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="599e6-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="599e6-105">ID</span><span class="sxs-lookup"><span data-stu-id="599e6-105">ID</span></span>|<span data-ttu-id="599e6-106">1035</span><span class="sxs-lookup"><span data-stu-id="599e6-106">1035</span></span>|  
|<span data-ttu-id="599e6-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="599e6-107">Keywords</span></span>|<span data-ttu-id="599e6-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="599e6-108">WFRuntime</span></span>|  
|<span data-ttu-id="599e6-109">Level</span><span class="sxs-lookup"><span data-stu-id="599e6-109">Level</span></span>|<span data-ttu-id="599e6-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="599e6-110">Verbose</span></span>|  
|<span data-ttu-id="599e6-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="599e6-111">Channel</span></span>|<span data-ttu-id="599e6-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="599e6-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="599e6-113">Description</span><span class="sxs-lookup"><span data-stu-id="599e6-113">Description</span></span>  

 <span data-ttu-id="599e6-114">Bir etkinliğin çalışma zamanı işlemini ayarlamış olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="599e6-114">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="599e6-115">İleti</span><span class="sxs-lookup"><span data-stu-id="599e6-115">Message</span></span>  

 <span data-ttu-id="599e6-116">Çalışma zamanı işlemi, DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' etkinliğine göre ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="599e6-116">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="599e6-117">Yürütme, DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğine yalıtılmış.</span><span class="sxs-lookup"><span data-stu-id="599e6-117">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="599e6-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="599e6-118">Details</span></span>  
  
|<span data-ttu-id="599e6-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="599e6-119">Data Item Name</span></span>|<span data-ttu-id="599e6-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="599e6-120">Data Item Type</span></span>|<span data-ttu-id="599e6-121">Description</span><span class="sxs-lookup"><span data-stu-id="599e6-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="599e6-122">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="599e6-122">Activity</span></span>|<span data-ttu-id="599e6-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="599e6-123">xs:string</span></span>|<span data-ttu-id="599e6-124">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="599e6-124">The type name of the activity.</span></span>|  
|<span data-ttu-id="599e6-125">DisplayName</span><span class="sxs-lookup"><span data-stu-id="599e6-125">DisplayName</span></span>|<span data-ttu-id="599e6-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="599e6-126">xs:string</span></span>|<span data-ttu-id="599e6-127">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="599e6-127">The display name of the activity.</span></span>|  
|<span data-ttu-id="599e6-128">InstanceId</span><span class="sxs-lookup"><span data-stu-id="599e6-128">InstanceId</span></span>|<span data-ttu-id="599e6-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="599e6-129">xs:string</span></span>|<span data-ttu-id="599e6-130">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="599e6-130">The instance id of the activity.</span></span>|  
|<span data-ttu-id="599e6-131">Isotedactivity</span><span class="sxs-lookup"><span data-stu-id="599e6-131">IsolatedActivity</span></span>|<span data-ttu-id="599e6-132">xs: String</span><span class="sxs-lookup"><span data-stu-id="599e6-132">xs:string</span></span>|<span data-ttu-id="599e6-133">İşlemin yalıtılmış olduğu etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="599e6-133">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="599e6-134">Isotedactivitydisplayname</span><span class="sxs-lookup"><span data-stu-id="599e6-134">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="599e6-135">xs: String</span><span class="sxs-lookup"><span data-stu-id="599e6-135">xs:string</span></span>|<span data-ttu-id="599e6-136">İşlemin yalıtılmış olduğu etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="599e6-136">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="599e6-137">Isotedactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="599e6-137">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="599e6-138">xs: String</span><span class="sxs-lookup"><span data-stu-id="599e6-138">xs:string</span></span>|<span data-ttu-id="599e6-139">İşlemin yalıtılmış olduğu etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="599e6-139">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="599e6-140">AppDomain</span><span class="sxs-lookup"><span data-stu-id="599e6-140">AppDomain</span></span>|<span data-ttu-id="599e6-141">xs: String</span><span class="sxs-lookup"><span data-stu-id="599e6-141">xs:string</span></span>|<span data-ttu-id="599e6-142">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="599e6-142">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
