---
description: 'Hakkında daha fazla bilgi edinin: 1028-Completetransactioncontextworkıtem'
title: 1028 - CompleteTransactionContextWorkItem
ms.date: 03/30/2017
ms.assetid: 95423f9d-d29a-460e-bcd8-096e80af5bd0
ms.openlocfilehash: ae66072769c24ce8d44f92a88cd4232d20bde5f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755466"
---
# <a name="1028---completetransactioncontextworkitem"></a><span data-ttu-id="b2702-103">1028 - CompleteTransactionContextWorkItem</span><span class="sxs-lookup"><span data-stu-id="b2702-103">1028 - CompleteTransactionContextWorkItem</span></span>

## <a name="properties"></a><span data-ttu-id="b2702-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b2702-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b2702-105">ID</span><span class="sxs-lookup"><span data-stu-id="b2702-105">ID</span></span>|<span data-ttu-id="b2702-106">1028</span><span class="sxs-lookup"><span data-stu-id="b2702-106">1028</span></span>|  
|<span data-ttu-id="b2702-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b2702-107">Keywords</span></span>|<span data-ttu-id="b2702-108">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="b2702-108">WFRuntime</span></span>|  
|<span data-ttu-id="b2702-109">Level</span><span class="sxs-lookup"><span data-stu-id="b2702-109">Level</span></span>|<span data-ttu-id="b2702-110">Ayrıntılı</span><span class="sxs-lookup"><span data-stu-id="b2702-110">Verbose</span></span>|  
|<span data-ttu-id="b2702-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="b2702-111">Channel</span></span>|<span data-ttu-id="b2702-112">Microsoft-Windows-Application Server-uygulamalar/hata ayıkla</span><span class="sxs-lookup"><span data-stu-id="b2702-112">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b2702-113">Description</span><span class="sxs-lookup"><span data-stu-id="b2702-113">Description</span></span>  

 <span data-ttu-id="b2702-114">Bir TransactionContextWorkItem 'ın tamamlandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b2702-114">Indicates a TransactionContextWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b2702-115">İleti</span><span class="sxs-lookup"><span data-stu-id="b2702-115">Message</span></span>  

 <span data-ttu-id="b2702-116">DisplayName: ' %2 ', InstanceId: ' %3 ' olan ' %1 ' Activity 'si için bir TransactionContextWorkItem tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="b2702-116">A TransactionContextWorkItem has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b2702-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b2702-117">Details</span></span>  
  
|<span data-ttu-id="b2702-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b2702-118">Data Item Name</span></span>|<span data-ttu-id="b2702-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b2702-119">Data Item Type</span></span>|<span data-ttu-id="b2702-120">Description</span><span class="sxs-lookup"><span data-stu-id="b2702-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b2702-121">Etkinlik</span><span class="sxs-lookup"><span data-stu-id="b2702-121">Activity</span></span>|<span data-ttu-id="b2702-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="b2702-122">xs:string</span></span>|<span data-ttu-id="b2702-123">Etkinliğin tür adı.</span><span class="sxs-lookup"><span data-stu-id="b2702-123">The type name of the activity.</span></span>|  
|<span data-ttu-id="b2702-124">DisplayName</span><span class="sxs-lookup"><span data-stu-id="b2702-124">DisplayName</span></span>|<span data-ttu-id="b2702-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="b2702-125">xs:string</span></span>|<span data-ttu-id="b2702-126">Etkinliğin görünen adı.</span><span class="sxs-lookup"><span data-stu-id="b2702-126">The display name of the activity.</span></span>|  
|<span data-ttu-id="b2702-127">InstanceId</span><span class="sxs-lookup"><span data-stu-id="b2702-127">InstanceId</span></span>|<span data-ttu-id="b2702-128">xs: String</span><span class="sxs-lookup"><span data-stu-id="b2702-128">xs:string</span></span>|<span data-ttu-id="b2702-129">Etkinliğin örnek kimliği.</span><span class="sxs-lookup"><span data-stu-id="b2702-129">The instance id of the activity.</span></span>|  
|<span data-ttu-id="b2702-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b2702-130">AppDomain</span></span>|<span data-ttu-id="b2702-131">xs: String</span><span class="sxs-lookup"><span data-stu-id="b2702-131">xs:string</span></span>|<span data-ttu-id="b2702-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b2702-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
