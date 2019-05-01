---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: 198e11dd94b0ad5cdc1e01c3611280754ca081d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924858"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="b85be-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="b85be-102">1035 - RuntimeTransactionSet</span></span>
## <a name="properties"></a><span data-ttu-id="b85be-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b85be-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b85be-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="b85be-104">ID</span></span>|<span data-ttu-id="b85be-105">1035</span><span class="sxs-lookup"><span data-stu-id="b85be-105">1035</span></span>|  
|<span data-ttu-id="b85be-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b85be-106">Keywords</span></span>|<span data-ttu-id="b85be-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b85be-107">WFRuntime</span></span>|  
|<span data-ttu-id="b85be-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b85be-108">Level</span></span>|<span data-ttu-id="b85be-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="b85be-109">Verbose</span></span>|  
|<span data-ttu-id="b85be-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b85be-110">Channel</span></span>|<span data-ttu-id="b85be-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="b85be-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b85be-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b85be-112">Description</span></span>  
 <span data-ttu-id="b85be-113">Bir etkinliğin çalışma zamanı işlem ayarladı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b85be-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b85be-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b85be-114">Message</span></span>  
 <span data-ttu-id="b85be-115">Çalışma zamanı işlem '%1', DisplayName etkinliği tarafından ayarlanmış: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="b85be-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="b85be-116">'%4', DisplayName etkinlik için yalıtılmış yürütme: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="b85be-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b85be-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b85be-117">Details</span></span>  
  
|<span data-ttu-id="b85be-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b85be-118">Data Item Name</span></span>|<span data-ttu-id="b85be-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b85be-119">Data Item Type</span></span>|<span data-ttu-id="b85be-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b85be-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b85be-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="b85be-121">Activity</span></span>|<span data-ttu-id="b85be-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="b85be-122">xs:string</span></span>|<span data-ttu-id="b85be-123">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="b85be-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="b85be-124">displayName</span><span class="sxs-lookup"><span data-stu-id="b85be-124">DisplayName</span></span>|<span data-ttu-id="b85be-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="b85be-125">xs:string</span></span>|<span data-ttu-id="b85be-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b85be-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="b85be-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b85be-127">InstanceId</span></span>|<span data-ttu-id="b85be-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="b85be-128">xs:string</span></span>|<span data-ttu-id="b85be-129">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="b85be-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b85be-130">IsolatedActivity</span><span class="sxs-lookup"><span data-stu-id="b85be-130">IsolatedActivity</span></span>|<span data-ttu-id="b85be-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="b85be-131">xs:string</span></span>|<span data-ttu-id="b85be-132">İşlem için yalıtılmış etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="b85be-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="b85be-133">IsolatedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="b85be-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="b85be-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="b85be-134">xs:string</span></span>|<span data-ttu-id="b85be-135">İşlem için yalıtılmış etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b85be-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="b85be-136">IsolatedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="b85be-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="b85be-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="b85be-137">xs:string</span></span>|<span data-ttu-id="b85be-138">İşlem için yalıtılmış etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="b85be-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="b85be-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b85be-139">AppDomain</span></span>|<span data-ttu-id="b85be-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="b85be-140">xs:string</span></span>|<span data-ttu-id="b85be-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b85be-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
