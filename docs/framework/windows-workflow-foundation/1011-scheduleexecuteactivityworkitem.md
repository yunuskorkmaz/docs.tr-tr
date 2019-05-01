---
title: 1011 - ScheduleExecuteActivityWorkItem
ms.date: 03/30/2017
ms.assetid: e503ae46-ad6b-4fcb-8c0e-146d59a8eff1
ms.openlocfilehash: 299d09b7c4db94a2e27378ba0cc3dfeb03734ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982260"
---
# <a name="1011---scheduleexecuteactivityworkitem"></a><span data-ttu-id="dcbd7-102">1011 - ScheduleExecuteActivityWorkItem</span><span class="sxs-lookup"><span data-stu-id="dcbd7-102">1011 - ScheduleExecuteActivityWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="dcbd7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="dcbd7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dcbd7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="dcbd7-104">ID</span></span>|<span data-ttu-id="dcbd7-105">1011</span><span class="sxs-lookup"><span data-stu-id="dcbd7-105">1011</span></span>|  
|<span data-ttu-id="dcbd7-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="dcbd7-106">Keywords</span></span>|<span data-ttu-id="dcbd7-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="dcbd7-107">WFRuntime</span></span>|  
|<span data-ttu-id="dcbd7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="dcbd7-108">Level</span></span>|<span data-ttu-id="dcbd7-109">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="dcbd7-109">Verbose</span></span>|  
|<span data-ttu-id="dcbd7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="dcbd7-110">Channel</span></span>|<span data-ttu-id="dcbd7-111">Microsoft Windows uygulaması sunucu-uygulamalar/hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="dcbd7-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="dcbd7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcbd7-112">Description</span></span>  
 <span data-ttu-id="dcbd7-113">Bir ExecuteActivityWorkItem zamanlandı gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcbd7-113">Indicates an ExecuteActivityWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="dcbd7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="dcbd7-114">Message</span></span>  
 <span data-ttu-id="dcbd7-115">'%1', DisplayName etkinliği için bir ExecuteActivityWorkItem zamanlandı: '%2', InstanceId: '%3'.</span><span class="sxs-lookup"><span data-stu-id="dcbd7-115">An ExecuteActivityWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="dcbd7-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="dcbd7-116">Details</span></span>  
  
|<span data-ttu-id="dcbd7-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="dcbd7-117">Data Item Name</span></span>|<span data-ttu-id="dcbd7-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="dcbd7-118">Data Item Type</span></span>|<span data-ttu-id="dcbd7-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcbd7-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="dcbd7-120">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="dcbd7-120">Activity</span></span>|<span data-ttu-id="dcbd7-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="dcbd7-121">xs:string</span></span>|<span data-ttu-id="dcbd7-122">Etkinlik türü adı.</span><span class="sxs-lookup"><span data-stu-id="dcbd7-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="dcbd7-123">displayName</span><span class="sxs-lookup"><span data-stu-id="dcbd7-123">DisplayName</span></span>|<span data-ttu-id="dcbd7-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="dcbd7-124">xs:string</span></span>|<span data-ttu-id="dcbd7-125">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="dcbd7-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="dcbd7-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="dcbd7-126">InstanceId</span></span>|<span data-ttu-id="dcbd7-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="dcbd7-127">xs:string</span></span>|<span data-ttu-id="dcbd7-128">Etkinlik örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="dcbd7-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="dcbd7-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="dcbd7-129">AppDomain</span></span>|<span data-ttu-id="dcbd7-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="dcbd7-130">xs:string</span></span>|<span data-ttu-id="dcbd7-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="dcbd7-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
