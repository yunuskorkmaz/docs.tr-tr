---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 435a6a4390d52555d353a25ac119934087cf9c87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="ad8d2-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="ad8d2-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="ad8d2-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ad8d2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad8d2-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ad8d2-104">ID</span></span>|<span data-ttu-id="ad8d2-105">3550</span><span class="sxs-lookup"><span data-stu-id="ad8d2-105">3550</span></span>|  
|<span data-ttu-id="ad8d2-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ad8d2-106">Keywords</span></span>|<span data-ttu-id="ad8d2-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="ad8d2-107">WFServices</span></span>|  
|<span data-ttu-id="ad8d2-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ad8d2-108">Level</span></span>|<span data-ttu-id="ad8d2-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="ad8d2-109">Information</span></span>|  
|<span data-ttu-id="ad8d2-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ad8d2-110">Channel</span></span>|<span data-ttu-id="ad8d2-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ad8d2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ad8d2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad8d2-112">Description</span></span>  
 <span data-ttu-id="ad8d2-113">Arabellekli alma başarısız oldu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad8d2-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="ad8d2-114">Hizmet örneği belirli bu işlemi hazır olduğunda işlem yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="ad8d2-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ad8d2-115">İleti</span><span class="sxs-lookup"><span data-stu-id="ad8d2-115">Message</span></span>  
 <span data-ttu-id="ad8d2-116">'%1' işlemi şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="ad8d2-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="ad8d2-117">Hizmet örneği belirli bu işlemi için hazır olduğunda, başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="ad8d2-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ad8d2-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ad8d2-118">Details</span></span>  
  
|<span data-ttu-id="ad8d2-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ad8d2-119">Data Item Name</span></span>|<span data-ttu-id="ad8d2-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ad8d2-120">Data Item Type</span></span>|<span data-ttu-id="ad8d2-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad8d2-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ad8d2-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="ad8d2-122">OperationName</span></span>|<span data-ttu-id="ad8d2-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="ad8d2-123">xs:string</span></span>|<span data-ttu-id="ad8d2-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="ad8d2-124">The name of the operation.</span></span>|  
|<span data-ttu-id="ad8d2-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ad8d2-125">AppDomain</span></span>|<span data-ttu-id="ad8d2-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="ad8d2-126">xs:string</span></span>|<span data-ttu-id="ad8d2-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ad8d2-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
