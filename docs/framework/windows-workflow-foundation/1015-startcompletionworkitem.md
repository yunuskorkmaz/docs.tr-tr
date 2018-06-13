---
title: 1015 - StartCompletionWorkItem
ms.date: 03/30/2017
ms.assetid: 96fd1d4e-c5d0-46ad-8a71-4b4b49ac7262
ms.openlocfilehash: 6a2d4c866ec7d43e8ae40b5616a97c3b7adf1843
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509640"
---
# <a name="1015---startcompletionworkitem"></a><span data-ttu-id="2c5dd-102">1015 - StartCompletionWorkItem</span><span class="sxs-lookup"><span data-stu-id="2c5dd-102">1015 - StartCompletionWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="2c5dd-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2c5dd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2c5dd-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="2c5dd-104">ID</span></span>|<span data-ttu-id="2c5dd-105">1015</span><span class="sxs-lookup"><span data-stu-id="2c5dd-105">1015</span></span>|  
|<span data-ttu-id="2c5dd-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="2c5dd-106">Keywords</span></span>|<span data-ttu-id="2c5dd-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="2c5dd-107">WFRuntime</span></span>|  
|<span data-ttu-id="2c5dd-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2c5dd-108">Level</span></span>|<span data-ttu-id="2c5dd-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="2c5dd-109">Verbose</span></span>|  
|<span data-ttu-id="2c5dd-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2c5dd-110">Channel</span></span>|<span data-ttu-id="2c5dd-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="2c5dd-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2c5dd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c5dd-112">Description</span></span>  
 <span data-ttu-id="2c5dd-113">Bir CompletionWorkItem yürütme başlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c5dd-113">Indicates a CompletionWorkItem is starting execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2c5dd-114">İleti</span><span class="sxs-lookup"><span data-stu-id="2c5dd-114">Message</span></span>  
 <span data-ttu-id="2c5dd-115">Üst etkinlik '%1', DisplayName için CompletionWorkItem yürütülmesi başlatılıyor: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="2c5dd-115">Starting execution of a CompletionWorkItem for parent Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span> <span data-ttu-id="2c5dd-116">'%4', DisplayName etkinliği tamamlandı: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="2c5dd-116">Completed Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2c5dd-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2c5dd-117">Details</span></span>  
  
|<span data-ttu-id="2c5dd-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2c5dd-118">Data Item Name</span></span>|<span data-ttu-id="2c5dd-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2c5dd-119">Data Item Type</span></span>|<span data-ttu-id="2c5dd-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c5dd-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2c5dd-121">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="2c5dd-121">ParentActivity</span></span>|<span data-ttu-id="2c5dd-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="2c5dd-122">xs:string</span></span>|<span data-ttu-id="2c5dd-123">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="2c5dd-123">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="2c5dd-124">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="2c5dd-124">ParentDisplayName</span></span>|<span data-ttu-id="2c5dd-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="2c5dd-125">xs:string</span></span>|<span data-ttu-id="2c5dd-126">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="2c5dd-126">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="2c5dd-127">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="2c5dd-127">ParentInstanceId</span></span>|<span data-ttu-id="2c5dd-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="2c5dd-128">xs:string</span></span>|<span data-ttu-id="2c5dd-129">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="2c5dd-129">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="2c5dd-130">CompletedActivity</span><span class="sxs-lookup"><span data-stu-id="2c5dd-130">CompletedActivity</span></span>|<span data-ttu-id="2c5dd-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="2c5dd-131">xs:string</span></span>|<span data-ttu-id="2c5dd-132">Tamamlanan etkinliğin türü adı.</span><span class="sxs-lookup"><span data-stu-id="2c5dd-132">The type name of the completed activity.</span></span>|  
|<span data-ttu-id="2c5dd-133">CompletedActivityDisplayName</span><span class="sxs-lookup"><span data-stu-id="2c5dd-133">CompletedActivityDisplayName</span></span>|<span data-ttu-id="2c5dd-134">xs: String</span><span class="sxs-lookup"><span data-stu-id="2c5dd-134">xs:string</span></span>|<span data-ttu-id="2c5dd-135">Tamamlanan etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="2c5dd-135">The display name of the completed activity.</span></span>|  
|<span data-ttu-id="2c5dd-136">CompletedActivityInstanceId</span><span class="sxs-lookup"><span data-stu-id="2c5dd-136">CompletedActivityInstanceId</span></span>|<span data-ttu-id="2c5dd-137">xs: String</span><span class="sxs-lookup"><span data-stu-id="2c5dd-137">xs:string</span></span>|<span data-ttu-id="2c5dd-138">Tamamlanan etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="2c5dd-138">The instance id of the completed activity.</span></span>|  
|<span data-ttu-id="2c5dd-139">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2c5dd-139">AppDomain</span></span>|<span data-ttu-id="2c5dd-140">xs: String</span><span class="sxs-lookup"><span data-stu-id="2c5dd-140">xs:string</span></span>|<span data-ttu-id="2c5dd-141">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2c5dd-141">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
