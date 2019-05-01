---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032272"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="15659-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="15659-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="15659-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="15659-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="15659-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="15659-104">ID</span></span>|<span data-ttu-id="15659-105">1015</span><span class="sxs-lookup"><span data-stu-id="15659-105">1015</span></span>|  
|<span data-ttu-id="15659-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="15659-106">Keywords</span></span>|<span data-ttu-id="15659-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="15659-107">WFRuntime</span></span>|  
|<span data-ttu-id="15659-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="15659-108">Level</span></span>|<span data-ttu-id="15659-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="15659-109">Verbose</span></span>|  
|<span data-ttu-id="15659-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="15659-110">Channel</span></span>|<span data-ttu-id="15659-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="15659-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="15659-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15659-112">Description</span></span>  
 <span data-ttu-id="15659-113">Bir CompletionWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="15659-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="15659-114">İleti</span><span class="sxs-lookup"><span data-stu-id="15659-114">Message</span></span>  
 <span data-ttu-id="15659-115">Üst etkinlik '%1', DisplayName için bir CompletionWorkItem yürütülmesi başlatılıyor: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="15659-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="15659-116">'%4', DisplayName etkinliği tamamlandı: '%5', InstanceId: '%6'.</span><span class="sxs-lookup"><span data-stu-id="15659-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="15659-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="15659-117">Details</span></span>  
  
|<span data-ttu-id="15659-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="15659-118">Data Item Name</span></span>|<span data-ttu-id="15659-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="15659-119">Data Item Type</span></span>|<span data-ttu-id="15659-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15659-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="15659-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="15659-121">ParentActivity</span></span>|<span data-ttu-id="15659-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="15659-122">xs:string</span></span>|<span data-ttu-id="15659-123">Üst etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="15659-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="15659-124">ParentDisplayName</span><span class="sxs-lookup"><span data-stu-id="15659-124">ParentDisplayName</span></span>|<span data-ttu-id="15659-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="15659-125">xs:string</span></span>|<span data-ttu-id="15659-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="15659-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="15659-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="15659-127">ParentInstanceId</span></span>|<span data-ttu-id="15659-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="15659-128">xs:string</span></span>|<span data-ttu-id="15659-129">Üst etkinliği örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="15659-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="15659-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="15659-130">CompletedActivity</span></span>|<span data-ttu-id="15659-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="15659-131">xs:string</span></span>|<span data-ttu-id="15659-132">Tamamlanan etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="15659-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="15659-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="15659-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="15659-134">xs:string</span><span class="sxs-lookup"><span data-stu-id="15659-134">xs:string</span></span>|<span data-ttu-id="15659-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="15659-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="15659-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="15659-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="15659-137">xs:string</span><span class="sxs-lookup"><span data-stu-id="15659-137">xs:string</span></span>|<span data-ttu-id="15659-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="15659-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="15659-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="15659-139">AppDomain</span></span>|<span data-ttu-id="15659-140">xs:string</span><span class="sxs-lookup"><span data-stu-id="15659-140">xs:string</span></span>|<span data-ttu-id="15659-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="15659-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
