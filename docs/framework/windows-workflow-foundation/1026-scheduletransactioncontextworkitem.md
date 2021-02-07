---
description: 'Hakkında daha fazla bilgi edinin: 1026-Scheduletransactioncontextworkıtem'
title: 1026 - ScheduleTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 0d5f86ba-ec21-4129-a726-5432e425384c
ms.openlocfilehash: 913af6903d38cea8f5c8d3e6e72dff04ff706195
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755492"
---
# <a name="1026---scheduletransactioncontextworkitem"></a><span data-ttu-id="326b0-103">1026 - ScheduleTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="326b0-103">1026 - ScheduleTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="326b0-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="326b0-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="326b0-105">ID</span><span class="sxs-lookup"><span data-stu-id="326b0-105">ID</span></span>|<span data-ttu-id="326b0-106">1026</span><span class="sxs-lookup"><span data-stu-id="326b0-106">1026</span></span>|  
|<span data-ttu-id="326b0-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="326b0-107">Keywords</span></span>|<span data-ttu-id="326b0-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="326b0-108">WFRuntime</span></span>|  
|<span data-ttu-id="326b0-109">Level</span><span class="sxs-lookup"><span data-stu-id="326b0-109">Level</span></span>|<span data-ttu-id="326b0-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="326b0-110">Verbose</span></span>|  
|<span data-ttu-id="326b0-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="326b0-111">Channel</span></span>|<span data-ttu-id="326b0-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="326b0-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="326b0-113">Description</span><span class="sxs-lookup"><span data-stu-id="326b0-113">Description</span></span>  

 <span data-ttu-id="326b0-114">Bir TransactionContextWorkItem zamanlandığı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="326b0-114">Indicates a TransactionContextWorkItem has been scheduled.</span></span>  
  
## <a name="message"></a><span data-ttu-id="326b0-115">İleti</span><span class="sxs-lookup"><span data-stu-id="326b0-115">Message</span></span>  

 <span data-ttu-id="326b0-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir TransactionContextWorkItem zamanlandı.</span><span class="sxs-lookup"><span data-stu-id="326b0-116">A TransactionContextWorkItem has been scheduled for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="326b0-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="326b0-117">Details</span></span>  
  
|<span data-ttu-id="326b0-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="326b0-118">Data Item Name</span></span>|<span data-ttu-id="326b0-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="326b0-119">Data Item Type</span></span>|<span data-ttu-id="326b0-120">Description</span><span class="sxs-lookup"><span data-stu-id="326b0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="326b0-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="326b0-121">Activity</span></span>|<span data-ttu-id="326b0-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="326b0-122">xs:string</span></span>|<span data-ttu-id="326b0-123">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="326b0-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="326b0-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="326b0-124">DisplayName</span></span>|<span data-ttu-id="326b0-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="326b0-125">xs:string</span></span>|<span data-ttu-id="326b0-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="326b0-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="326b0-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="326b0-127">InstanceId</span></span>|<span data-ttu-id="326b0-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="326b0-128">xs:string</span></span>|<span data-ttu-id="326b0-129">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="326b0-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="326b0-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="326b0-130">AppDomain</span></span>|<span data-ttu-id="326b0-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="326b0-131">xs:string</span></span>|<span data-ttu-id="326b0-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="326b0-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
