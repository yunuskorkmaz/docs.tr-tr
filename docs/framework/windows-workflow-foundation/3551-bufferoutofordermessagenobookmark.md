---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755538"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="16ecd-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="16ecd-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="16ecd-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="16ecd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16ecd-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="16ecd-104">ID</span></span>|<span data-ttu-id="16ecd-105">3551</span><span class="sxs-lookup"><span data-stu-id="16ecd-105">3551</span></span>|  
|<span data-ttu-id="16ecd-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="16ecd-106">Keywords</span></span>|<span data-ttu-id="16ecd-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="16ecd-107">WFServices</span></span>|  
|<span data-ttu-id="16ecd-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="16ecd-108">Level</span></span>|<span data-ttu-id="16ecd-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="16ecd-109">Information</span></span>|  
|<span data-ttu-id="16ecd-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="16ecd-110">Channel</span></span>|<span data-ttu-id="16ecd-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="16ecd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="16ecd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16ecd-112">Description</span></span>  
 <span data-ttu-id="16ecd-113">Bir yer imi sürdürme başarısız oldu gösterir.</span><span class="sxs-lookup"><span data-stu-id="16ecd-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="16ecd-114">Arabellekli alma işlemi hizmet örneği bu belirli bir işlemi hazır olduğunda tekrar denenecek.</span><span class="sxs-lookup"><span data-stu-id="16ecd-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="16ecd-115">İleti</span><span class="sxs-lookup"><span data-stu-id="16ecd-115">Message</span></span>  
 <span data-ttu-id="16ecd-116">Hizmet örneği '%1' üzerinde '%2' işlemi şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="16ecd-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="16ecd-117">Hizmet örneği bu belirli bir işlemi hazır olduğunda başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="16ecd-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="16ecd-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="16ecd-118">Details</span></span>  
  
|<span data-ttu-id="16ecd-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="16ecd-119">Data Item Name</span></span>|<span data-ttu-id="16ecd-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="16ecd-120">Data Item Type</span></span>|<span data-ttu-id="16ecd-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16ecd-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="16ecd-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="16ecd-122">OperationName</span></span>|<span data-ttu-id="16ecd-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="16ecd-123">xs:string</span></span>|<span data-ttu-id="16ecd-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="16ecd-124">The name of the operation.</span></span>|  
|<span data-ttu-id="16ecd-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="16ecd-125">ServiceInstanceId</span></span>|<span data-ttu-id="16ecd-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="16ecd-126">xs:string</span></span>|<span data-ttu-id="16ecd-127">Hizmet örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="16ecd-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="16ecd-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="16ecd-128">AppDomain</span></span>|<span data-ttu-id="16ecd-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="16ecd-129">xs:string</span></span>|<span data-ttu-id="16ecd-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="16ecd-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
