---
title: 1035 - RuntimeTransactionSet
ms.date: 03/30/2017
ms.assetid: 03b37de9-778c-4beb-b0e3-de73ece6088e
ms.openlocfilehash: b8bf8431c4e2b82c6aac95820eb45de2a404e976
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294280"
---
# <a name="1035---runtimetransactionset"></a><span data-ttu-id="dade3-102">1035 - RuntimeTransactionSet</span><span class="sxs-lookup"><span data-stu-id="dade3-102">1035 - RuntimeTransactionSet</span></span>

## <a name="properties"></a><span data-ttu-id="dade3-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="dade3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dade3-104">ID</span><span class="sxs-lookup"><span data-stu-id="dade3-104">ID</span></span>|<span data-ttu-id="dade3-105">1035</span><span class="sxs-lookup"><span data-stu-id="dade3-105">1035</span></span>|  
|<span data-ttu-id="dade3-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="dade3-106">Keywords</span></span>|<span data-ttu-id="dade3-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="dade3-107">WFRuntime</span></span>|  
|<span data-ttu-id="dade3-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="dade3-108">Level</span></span>|<span data-ttu-id="dade3-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="dade3-109">Verbose</span></span>|  
|<span data-ttu-id="dade3-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="dade3-110">Channel</span></span>|<span data-ttu-id="dade3-111">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="dade3-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dade3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dade3-112">Description</span></span>  

 <span data-ttu-id="dade3-113">Bir etkinliğin çalışma zamanı işlemini ayarlamış olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dade3-113">Indicates an activity has set the runtime transaction.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dade3-114">İleti</span><span class="sxs-lookup"><span data-stu-id="dade3-114">Message</span></span>  

 <span data-ttu-id="dade3-115">Çalışma zamanı işlemi, DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' etkinliğine göre ayarlandı.</span><span class="sxs-lookup"><span data-stu-id="dade3-115">The runtime transaction has been set by Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  <span data-ttu-id="dade3-116">Yürütme, DisplayName: ' %5 ', InstanceId: ' %6 ' olan ' %4 ' etkinliğine yalıtılmış.</span><span class="sxs-lookup"><span data-stu-id="dade3-116">Execution isolated to Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dade3-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="dade3-117">Details</span></span>  
  
|<span data-ttu-id="dade3-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="dade3-118">Data Item Name</span></span>|<span data-ttu-id="dade3-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="dade3-119">Data Item Type</span></span>|<span data-ttu-id="dade3-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dade3-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dade3-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="dade3-121">Activity</span></span>|<span data-ttu-id="dade3-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="dade3-122">xs:string</span></span>|<span data-ttu-id="dade3-123">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="dade3-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="dade3-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="dade3-124">DisplayName</span></span>|<span data-ttu-id="dade3-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="dade3-125">xs:string</span></span>|<span data-ttu-id="dade3-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="dade3-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="dade3-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="dade3-127">InstanceId</span></span>|<span data-ttu-id="dade3-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="dade3-128">xs:string</span></span>|<span data-ttu-id="dade3-129">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="dade3-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="dade3-130">Isotedactivity</span><span class="sxs-lookup"><span data-stu-id="dade3-130">IsolatedActivity</span></span>|<span data-ttu-id="dade3-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="dade3-131">xs:string</span></span>|<span data-ttu-id="dade3-132">İşlemin yalıtılmış olduğu etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="dade3-132">The type name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="dade3-133">Isotedactivitydisplayname</span><span class="sxs-lookup"><span data-stu-id="dade3-133">IsolatedActivityDisplayName</span></span>|<span data-ttu-id="dade3-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="dade3-134">xs:string</span></span>|<span data-ttu-id="dade3-135">İşlemin yalıtılmış olduğu etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="dade3-135">The display name of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="dade3-136">Isotedactivityınstanceıd</span><span class="sxs-lookup"><span data-stu-id="dade3-136">IsolatedActivityInstanceId</span></span>|<span data-ttu-id="dade3-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="dade3-137">xs:string</span></span>|<span data-ttu-id="dade3-138">İşlemin yalıtılmış olduğu etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="dade3-138">The instance id of the activity that the transaction is isolated to.</span></span>|  
|<span data-ttu-id="dade3-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dade3-139">AppDomain</span></span>|<span data-ttu-id="dade3-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="dade3-140">xs:string</span></span>|<span data-ttu-id="dade3-141">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="dade3-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
