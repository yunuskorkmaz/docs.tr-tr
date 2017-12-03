---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc505a4e0e79b37f9adff41b80dcba55215576f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="8eb1c-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="8eb1c-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="8eb1c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8eb1c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8eb1c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="8eb1c-104">ID</span></span>|<span data-ttu-id="8eb1c-105">3551</span><span class="sxs-lookup"><span data-stu-id="8eb1c-105">3551</span></span>|  
|<span data-ttu-id="8eb1c-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="8eb1c-106">Keywords</span></span>|<span data-ttu-id="8eb1c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="8eb1c-107">WFServices</span></span>|  
|<span data-ttu-id="8eb1c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="8eb1c-108">Level</span></span>|<span data-ttu-id="8eb1c-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="8eb1c-109">Information</span></span>|  
|<span data-ttu-id="8eb1c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="8eb1c-110">Channel</span></span>|<span data-ttu-id="8eb1c-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="8eb1c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8eb1c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eb1c-112">Description</span></span>  
 <span data-ttu-id="8eb1c-113">Yer işareti sürdürme başarısız oldu gösterir.</span><span class="sxs-lookup"><span data-stu-id="8eb1c-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="8eb1c-114">Arabellekli alma işlemi hizmet örneği belirli bu işlemi hazır olduğunda yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="8eb1c-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8eb1c-115">İleti</span><span class="sxs-lookup"><span data-stu-id="8eb1c-115">Message</span></span>  
 <span data-ttu-id="8eb1c-116">Hizmet örneği '%1' işlemi '%2', şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="8eb1c-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="8eb1c-117">Hizmet örneği belirli bu işlemi için hazır olduğunda, başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="8eb1c-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8eb1c-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8eb1c-118">Details</span></span>  
  
|<span data-ttu-id="8eb1c-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8eb1c-119">Data Item Name</span></span>|<span data-ttu-id="8eb1c-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8eb1c-120">Data Item Type</span></span>|<span data-ttu-id="8eb1c-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eb1c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8eb1c-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="8eb1c-122">OperationName</span></span>|<span data-ttu-id="8eb1c-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="8eb1c-123">xs:string</span></span>|<span data-ttu-id="8eb1c-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="8eb1c-124">The name of the operation.</span></span>|  
|<span data-ttu-id="8eb1c-125">Serviceınstanceıd</span><span class="sxs-lookup"><span data-stu-id="8eb1c-125">ServiceInstanceId</span></span>|<span data-ttu-id="8eb1c-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="8eb1c-126">xs:string</span></span>|<span data-ttu-id="8eb1c-127">Hizmet örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="8eb1c-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="8eb1c-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8eb1c-128">AppDomain</span></span>|<span data-ttu-id="8eb1c-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="8eb1c-129">xs:string</span></span>|<span data-ttu-id="8eb1c-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8eb1c-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
