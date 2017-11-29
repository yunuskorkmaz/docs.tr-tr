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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ce8b2cd52523d8a2efc94214479ca3c41d2dec4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="66210-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="66210-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="66210-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="66210-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66210-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="66210-104">ID</span></span>|<span data-ttu-id="66210-105">3550</span><span class="sxs-lookup"><span data-stu-id="66210-105">3550</span></span>|  
|<span data-ttu-id="66210-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="66210-106">Keywords</span></span>|<span data-ttu-id="66210-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="66210-107">WFServices</span></span>|  
|<span data-ttu-id="66210-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="66210-108">Level</span></span>|<span data-ttu-id="66210-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="66210-109">Information</span></span>|  
|<span data-ttu-id="66210-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="66210-110">Channel</span></span>|<span data-ttu-id="66210-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="66210-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="66210-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66210-112">Description</span></span>  
 <span data-ttu-id="66210-113">Arabellekli alma başarısız oldu gösterir.</span><span class="sxs-lookup"><span data-stu-id="66210-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="66210-114">Hizmet örneği belirli bu işlemi hazır olduğunda işlem yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="66210-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="66210-115">İleti</span><span class="sxs-lookup"><span data-stu-id="66210-115">Message</span></span>  
 <span data-ttu-id="66210-116">'%1' işlemi şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="66210-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="66210-117">Hizmet örneği belirli bu işlemi için hazır olduğunda, başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="66210-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="66210-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="66210-118">Details</span></span>  
  
|<span data-ttu-id="66210-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="66210-119">Data Item Name</span></span>|<span data-ttu-id="66210-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="66210-120">Data Item Type</span></span>|<span data-ttu-id="66210-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66210-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="66210-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="66210-122">OperationName</span></span>|<span data-ttu-id="66210-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="66210-123">xs:string</span></span>|<span data-ttu-id="66210-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="66210-124">The name of the operation.</span></span>|  
|<span data-ttu-id="66210-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="66210-125">AppDomain</span></span>|<span data-ttu-id="66210-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="66210-126">xs:string</span></span>|<span data-ttu-id="66210-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="66210-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
