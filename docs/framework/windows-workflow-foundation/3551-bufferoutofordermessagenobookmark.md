---
description: 'Hakkında daha fazla bilgi edinin: 3551-BufferOutOfOrderMessageNoBookmark'
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 573056fed1753ac55c51d9a074047e8eea15e229
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778002"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="3e728-103">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="3e728-103">3551 - BufferOutOfOrderMessageNoBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="3e728-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3e728-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3e728-105">ID</span><span class="sxs-lookup"><span data-stu-id="3e728-105">ID</span></span>|<span data-ttu-id="3e728-106">3551</span><span class="sxs-lookup"><span data-stu-id="3e728-106">3551</span></span>|  
|<span data-ttu-id="3e728-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="3e728-107">Keywords</span></span>|<span data-ttu-id="3e728-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="3e728-108">WFServices</span></span>|  
|<span data-ttu-id="3e728-109">Level</span><span class="sxs-lookup"><span data-stu-id="3e728-109">Level</span></span>|<span data-ttu-id="3e728-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="3e728-110">Information</span></span>|  
|<span data-ttu-id="3e728-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="3e728-111">Channel</span></span>|<span data-ttu-id="3e728-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="3e728-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3e728-113">Description</span><span class="sxs-lookup"><span data-stu-id="3e728-113">Description</span></span>  

 <span data-ttu-id="3e728-114">Sürdürme yer işaretinin başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e728-114">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="3e728-115">Hizmet örneği bu işlemi işlemeye hazırsa, arabelleğe alınmış alma işlemi yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="3e728-115">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3e728-116">İleti</span><span class="sxs-lookup"><span data-stu-id="3e728-116">Message</span></span>  

 <span data-ttu-id="3e728-117">' %1 ' hizmet örneğindeki ' %2 ' işlemi şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="3e728-117">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="3e728-118">Hizmet örneği bu işlemi işlemeye hazırsa başka bir girişim yapılacak.</span><span class="sxs-lookup"><span data-stu-id="3e728-118">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3e728-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3e728-119">Details</span></span>  
  
|<span data-ttu-id="3e728-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="3e728-120">Data Item Name</span></span>|<span data-ttu-id="3e728-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="3e728-121">Data Item Type</span></span>|<span data-ttu-id="3e728-122">Description</span><span class="sxs-lookup"><span data-stu-id="3e728-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3e728-123">OperationName</span><span class="sxs-lookup"><span data-stu-id="3e728-123">OperationName</span></span>|<span data-ttu-id="3e728-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="3e728-124">xs:string</span></span>|<span data-ttu-id="3e728-125">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="3e728-125">The name of the operation.</span></span>|  
|<span data-ttu-id="3e728-126">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="3e728-126">ServiceInstanceId</span></span>|<span data-ttu-id="3e728-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="3e728-127">xs:string</span></span>|<span data-ttu-id="3e728-128">Hizmet örneğinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="3e728-128">The id of the service instance.</span></span>|  
|<span data-ttu-id="3e728-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3e728-129">AppDomain</span></span>|<span data-ttu-id="3e728-130">xs: String</span><span class="sxs-lookup"><span data-stu-id="3e728-130">xs:string</span></span>|<span data-ttu-id="3e728-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="3e728-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
