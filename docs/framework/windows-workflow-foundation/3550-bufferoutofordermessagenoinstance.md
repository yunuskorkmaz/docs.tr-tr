---
description: ': 3550-Bufferoutofordermessagenoınstance hakkında daha fazla bilgi edinin'
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: cb51f9fa32de1b56560f9593dae2ec82c100dc65
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631456"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="5c486-103">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="5c486-103">3550 - BufferOutOfOrderMessageNoInstance</span></span>

## <a name="properties"></a><span data-ttu-id="5c486-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5c486-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5c486-105">ID</span><span class="sxs-lookup"><span data-stu-id="5c486-105">ID</span></span>|<span data-ttu-id="5c486-106">3550</span><span class="sxs-lookup"><span data-stu-id="5c486-106">3550</span></span>|  
|<span data-ttu-id="5c486-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="5c486-107">Keywords</span></span>|<span data-ttu-id="5c486-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="5c486-108">WFServices</span></span>|  
|<span data-ttu-id="5c486-109">Level</span><span class="sxs-lookup"><span data-stu-id="5c486-109">Level</span></span>|<span data-ttu-id="5c486-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="5c486-110">Information</span></span>|  
|<span data-ttu-id="5c486-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="5c486-111">Channel</span></span>|<span data-ttu-id="5c486-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="5c486-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5c486-113">Description</span><span class="sxs-lookup"><span data-stu-id="5c486-113">Description</span></span>  

 <span data-ttu-id="5c486-114">Arabelleğe alınan bir alma başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5c486-114">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="5c486-115">Hizmet örneği bu belirli işlemi işlemeye hazırsa işlem yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="5c486-115">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5c486-116">İleti</span><span class="sxs-lookup"><span data-stu-id="5c486-116">Message</span></span>  

 <span data-ttu-id="5c486-117">' %1 ' işlemi şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="5c486-117">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="5c486-118">Hizmet örneği bu işlemi işlemeye hazırsa başka bir girişim yapılacak.</span><span class="sxs-lookup"><span data-stu-id="5c486-118">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5c486-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5c486-119">Details</span></span>  
  
|<span data-ttu-id="5c486-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="5c486-120">Data Item Name</span></span>|<span data-ttu-id="5c486-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="5c486-121">Data Item Type</span></span>|<span data-ttu-id="5c486-122">Description</span><span class="sxs-lookup"><span data-stu-id="5c486-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5c486-123">OperationName</span><span class="sxs-lookup"><span data-stu-id="5c486-123">OperationName</span></span>|<span data-ttu-id="5c486-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="5c486-124">xs:string</span></span>|<span data-ttu-id="5c486-125">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="5c486-125">The name of the operation.</span></span>|  
|<span data-ttu-id="5c486-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5c486-126">AppDomain</span></span>|<span data-ttu-id="5c486-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="5c486-127">xs:string</span></span>|<span data-ttu-id="5c486-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="5c486-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
