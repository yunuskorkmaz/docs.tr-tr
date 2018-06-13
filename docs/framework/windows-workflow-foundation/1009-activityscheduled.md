---
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 0e3ea53a7b0509fcb8b73b61193742d615ac7e91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509978"
---
# <a name="1009---activityscheduled"></a><span data-ttu-id="a44f7-102">1009 - ActivityScheduled</span><span class="sxs-lookup"><span data-stu-id="a44f7-102">1009 - ActivityScheduled</span></span>
## <a name="properties"></a><span data-ttu-id="a44f7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a44f7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a44f7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a44f7-104">ID</span></span>|<span data-ttu-id="a44f7-105">1009</span><span class="sxs-lookup"><span data-stu-id="a44f7-105">1009</span></span>|  
|<span data-ttu-id="a44f7-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a44f7-106">Keywords</span></span>|<span data-ttu-id="a44f7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="a44f7-107">WFRuntime</span></span>|  
|<span data-ttu-id="a44f7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a44f7-108">Level</span></span>|<span data-ttu-id="a44f7-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="a44f7-109">Information</span></span>|  
|<span data-ttu-id="a44f7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a44f7-110">Channel</span></span>|<span data-ttu-id="a44f7-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="a44f7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a44f7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a44f7-112">Description</span></span>  
 <span data-ttu-id="a44f7-113">Bir etkinlik çalıştırılmak üzere zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="a44f7-113">Indicates an activity is being scheduled for execution.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a44f7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a44f7-114">Message</span></span>  
 <span data-ttu-id="a44f7-115">Üst etkinlik '%1', DisplayName: '%2', örnek kimliği: '%3' zamanlanmış alt etkinliği '%4', DisplayName: '%5', örnek kimliği: '%6'.</span><span class="sxs-lookup"><span data-stu-id="a44f7-115">Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a44f7-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a44f7-116">Details</span></span>  
  
|<span data-ttu-id="a44f7-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a44f7-117">Data Item Name</span></span>|<span data-ttu-id="a44f7-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a44f7-118">Data Item Type</span></span>|<span data-ttu-id="a44f7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a44f7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a44f7-120">ParentActivity</span><span class="sxs-lookup"><span data-stu-id="a44f7-120">ParentActivity</span></span>|<span data-ttu-id="a44f7-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="a44f7-121">xs:string</span></span>|<span data-ttu-id="a44f7-122">Üst etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="a44f7-122">The type name of the parent activity.</span></span>|  
|<span data-ttu-id="a44f7-123">Ana görüntü adı</span><span class="sxs-lookup"><span data-stu-id="a44f7-123">ParentDisplayName</span></span>|<span data-ttu-id="a44f7-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="a44f7-124">xs:string</span></span>|<span data-ttu-id="a44f7-125">Üst etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a44f7-125">The display name of the parent activity.</span></span>|  
|<span data-ttu-id="a44f7-126">ParentInstanceId</span><span class="sxs-lookup"><span data-stu-id="a44f7-126">ParentInstanceId</span></span>|<span data-ttu-id="a44f7-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="a44f7-127">xs:string</span></span>|<span data-ttu-id="a44f7-128">Üst etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="a44f7-128">The instance id of the parent activity.</span></span>|  
|<span data-ttu-id="a44f7-129">ChildActivity</span><span class="sxs-lookup"><span data-stu-id="a44f7-129">ChildActivity</span></span>|<span data-ttu-id="a44f7-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="a44f7-130">xs:string</span></span>|<span data-ttu-id="a44f7-131">Zamanlanmış alt etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="a44f7-131">The type name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="a44f7-132">ChildDisplayName</span><span class="sxs-lookup"><span data-stu-id="a44f7-132">ChildDisplayName</span></span>|<span data-ttu-id="a44f7-133">xs: String</span><span class="sxs-lookup"><span data-stu-id="a44f7-133">xs:string</span></span>|<span data-ttu-id="a44f7-134">Zamanlanmış alt etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="a44f7-134">The display name of the scheduled child activity.</span></span>|  
|<span data-ttu-id="a44f7-135">ChildInstanceId</span><span class="sxs-lookup"><span data-stu-id="a44f7-135">ChildInstanceId</span></span>|<span data-ttu-id="a44f7-136">xs: String</span><span class="sxs-lookup"><span data-stu-id="a44f7-136">xs:string</span></span>|<span data-ttu-id="a44f7-137">Zamanlanmış alt etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="a44f7-137">The instance id of the scheduled child activity.</span></span>|  
|<span data-ttu-id="a44f7-138">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a44f7-138">AppDomain</span></span>|<span data-ttu-id="a44f7-139">xs: String</span><span class="sxs-lookup"><span data-stu-id="a44f7-139">xs:string</span></span>|<span data-ttu-id="a44f7-140">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a44f7-140">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
