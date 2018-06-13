---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512238"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="ef878-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="ef878-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="ef878-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ef878-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ef878-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ef878-104">ID</span></span>|<span data-ttu-id="ef878-105">3551</span><span class="sxs-lookup"><span data-stu-id="ef878-105">3551</span></span>|  
|<span data-ttu-id="ef878-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ef878-106">Keywords</span></span>|<span data-ttu-id="ef878-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="ef878-107">WFServices</span></span>|  
|<span data-ttu-id="ef878-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ef878-108">Level</span></span>|<span data-ttu-id="ef878-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="ef878-109">Information</span></span>|  
|<span data-ttu-id="ef878-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ef878-110">Channel</span></span>|<span data-ttu-id="ef878-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ef878-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ef878-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef878-112">Description</span></span>  
 <span data-ttu-id="ef878-113">Yer işareti sürdürme başarısız oldu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef878-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="ef878-114">Arabellekli alma işlemi hizmet örneği belirli bu işlemi hazır olduğunda yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="ef878-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ef878-115">İleti</span><span class="sxs-lookup"><span data-stu-id="ef878-115">Message</span></span>  
 <span data-ttu-id="ef878-116">Hizmet örneği '%1' işlemi '%2', şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="ef878-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="ef878-117">Hizmet örneği belirli bu işlemi için hazır olduğunda, başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="ef878-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ef878-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ef878-118">Details</span></span>  
  
|<span data-ttu-id="ef878-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ef878-119">Data Item Name</span></span>|<span data-ttu-id="ef878-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ef878-120">Data Item Type</span></span>|<span data-ttu-id="ef878-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ef878-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ef878-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="ef878-122">OperationName</span></span>|<span data-ttu-id="ef878-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="ef878-123">xs:string</span></span>|<span data-ttu-id="ef878-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="ef878-124">The name of the operation.</span></span>|  
|<span data-ttu-id="ef878-125">Serviceınstanceıd</span><span class="sxs-lookup"><span data-stu-id="ef878-125">ServiceInstanceId</span></span>|<span data-ttu-id="ef878-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="ef878-126">xs:string</span></span>|<span data-ttu-id="ef878-127">Hizmet örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="ef878-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="ef878-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ef878-128">AppDomain</span></span>|<span data-ttu-id="ef878-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="ef878-129">xs:string</span></span>|<span data-ttu-id="ef878-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ef878-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
