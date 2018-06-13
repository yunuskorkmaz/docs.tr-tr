---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 299d09b7c4db94a2e27378ba0cc3dfeb03734ab4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509622"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="4398e-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="4398e-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="4398e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4398e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4398e-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="4398e-104">ID</span></span>|<span data-ttu-id="4398e-105">1011</span><span class="sxs-lookup"><span data-stu-id="4398e-105">1011</span></span>|  
|<span data-ttu-id="4398e-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="4398e-106">Keywords</span></span>|<span data-ttu-id="4398e-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="4398e-107">WFRuntime</span></span>|  
|<span data-ttu-id="4398e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4398e-108">Level</span></span>|<span data-ttu-id="4398e-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="4398e-109">Verbose</span></span>|  
|<span data-ttu-id="4398e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4398e-110">Channel</span></span>|<span data-ttu-id="4398e-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="4398e-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4398e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4398e-112">Description</span></span>  
 <span data-ttu-id="4398e-113">Bir ExecuteActivityWorkItem zamanlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="4398e-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4398e-114">İleti</span><span class="sxs-lookup"><span data-stu-id="4398e-114">Message</span></span>  
 <span data-ttu-id="4398e-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem zamanlandı: '%2', örnek kimliği: '%3'.</span><span class="sxs-lookup"><span data-stu-id="4398e-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4398e-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4398e-116">Details</span></span>  
  
|<span data-ttu-id="4398e-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4398e-117">Data Item Name</span></span>|<span data-ttu-id="4398e-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4398e-118">Data Item Type</span></span>|<span data-ttu-id="4398e-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4398e-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4398e-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="4398e-120">Activity</span></span>|<span data-ttu-id="4398e-121">xs: String</span><span class="sxs-lookup"><span data-stu-id="4398e-121">xs:string</span></span>|<span data-ttu-id="4398e-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="4398e-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="4398e-123">Görünen adı</span><span class="sxs-lookup"><span data-stu-id="4398e-123">DisplayName</span></span>|<span data-ttu-id="4398e-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="4398e-124">xs:string</span></span>|<span data-ttu-id="4398e-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="4398e-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="4398e-126">örnek kimliği</span><span class="sxs-lookup"><span data-stu-id="4398e-126">InstanceId</span></span>|<span data-ttu-id="4398e-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="4398e-127">xs:string</span></span>|<span data-ttu-id="4398e-128">Etkinlik örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="4398e-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="4398e-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4398e-129">AppDomain</span></span>|<span data-ttu-id="4398e-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="4398e-130">xs:string</span></span>|<span data-ttu-id="4398e-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4398e-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
