---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 5e6a5f9d21435fee8309bd222443407e50ec2cee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263613"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="7448e-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="7448e-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="7448e-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7448e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7448e-104">ID</span><span class="sxs-lookup"><span data-stu-id="7448e-104">ID</span></span>|<span data-ttu-id="7448e-105">3551</span><span class="sxs-lookup"><span data-stu-id="7448e-105">3551</span></span>|  
|<span data-ttu-id="7448e-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="7448e-106">Keywords</span></span>|<span data-ttu-id="7448e-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="7448e-107">WFServices</span></span>|  
|<span data-ttu-id="7448e-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="7448e-108">Level</span></span>|<span data-ttu-id="7448e-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="7448e-109">Information</span></span>|  
|<span data-ttu-id="7448e-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="7448e-110">Channel</span></span>|<span data-ttu-id="7448e-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="7448e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7448e-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7448e-112">Description</span></span>  

 <span data-ttu-id="7448e-113">Sürdürme yer işaretinin başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7448e-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="7448e-114">Hizmet örneği bu işlemi işlemeye hazırsa, arabelleğe alınmış alma işlemi yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="7448e-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7448e-115">İleti</span><span class="sxs-lookup"><span data-stu-id="7448e-115">Message</span></span>  

 <span data-ttu-id="7448e-116">' %1 ' hizmet örneğindeki ' %2 ' işlemi şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="7448e-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="7448e-117">Hizmet örneği bu işlemi işlemeye hazırsa başka bir girişim yapılacak.</span><span class="sxs-lookup"><span data-stu-id="7448e-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7448e-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7448e-118">Details</span></span>  
  
|<span data-ttu-id="7448e-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="7448e-119">Data Item Name</span></span>|<span data-ttu-id="7448e-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="7448e-120">Data Item Type</span></span>|<span data-ttu-id="7448e-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7448e-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7448e-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="7448e-122">OperationName</span></span>|<span data-ttu-id="7448e-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="7448e-123">xs:string</span></span>|<span data-ttu-id="7448e-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="7448e-124">The name of the operation.</span></span>|  
|<span data-ttu-id="7448e-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="7448e-125">ServiceInstanceId</span></span>|<span data-ttu-id="7448e-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="7448e-126">xs:string</span></span>|<span data-ttu-id="7448e-127">Hizmet örneğinin kimliği.</span><span class="sxs-lookup"><span data-stu-id="7448e-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="7448e-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7448e-128">AppDomain</span></span>|<span data-ttu-id="7448e-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="7448e-129">xs:string</span></span>|<span data-ttu-id="7448e-130">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="7448e-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
