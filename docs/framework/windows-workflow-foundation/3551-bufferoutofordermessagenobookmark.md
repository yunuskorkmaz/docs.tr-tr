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
ms.workload: dotnet
ms.openlocfilehash: 5e785e40afcb91620940f952022eda4c4b799f4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="0e408-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="0e408-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>
## <a name="properties"></a><span data-ttu-id="0e408-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0e408-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0e408-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="0e408-104">ID</span></span>|<span data-ttu-id="0e408-105">3551</span><span class="sxs-lookup"><span data-stu-id="0e408-105">3551</span></span>|  
|<span data-ttu-id="0e408-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="0e408-106">Keywords</span></span>|<span data-ttu-id="0e408-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="0e408-107">WFServices</span></span>|  
|<span data-ttu-id="0e408-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="0e408-108">Level</span></span>|<span data-ttu-id="0e408-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="0e408-109">Information</span></span>|  
|<span data-ttu-id="0e408-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="0e408-110">Channel</span></span>|<span data-ttu-id="0e408-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="0e408-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0e408-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e408-112">Description</span></span>  
 <span data-ttu-id="0e408-113">Yer işareti sürdürme başarısız oldu gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e408-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="0e408-114">Arabellekli alma işlemi hizmet örneği belirli bu işlemi hazır olduğunda yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="0e408-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0e408-115">İleti</span><span class="sxs-lookup"><span data-stu-id="0e408-115">Message</span></span>  
 <span data-ttu-id="0e408-116">Hizmet örneği '%1' işlemi '%2', şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="0e408-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="0e408-117">Hizmet örneği belirli bu işlemi için hazır olduğunda, başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="0e408-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0e408-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0e408-118">Details</span></span>  
  
|<span data-ttu-id="0e408-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="0e408-119">Data Item Name</span></span>|<span data-ttu-id="0e408-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="0e408-120">Data Item Type</span></span>|<span data-ttu-id="0e408-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e408-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0e408-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="0e408-122">OperationName</span></span>|<span data-ttu-id="0e408-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="0e408-123">xs:string</span></span>|<span data-ttu-id="0e408-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="0e408-124">The name of the operation.</span></span>|  
|<span data-ttu-id="0e408-125">Serviceınstanceıd</span><span class="sxs-lookup"><span data-stu-id="0e408-125">ServiceInstanceId</span></span>|<span data-ttu-id="0e408-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="0e408-126">xs:string</span></span>|<span data-ttu-id="0e408-127">Hizmet örneği kimliği.</span><span class="sxs-lookup"><span data-stu-id="0e408-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="0e408-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0e408-128">AppDomain</span></span>|<span data-ttu-id="0e408-129">xs: String</span><span class="sxs-lookup"><span data-stu-id="0e408-129">xs:string</span></span>|<span data-ttu-id="0e408-130">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0e408-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
