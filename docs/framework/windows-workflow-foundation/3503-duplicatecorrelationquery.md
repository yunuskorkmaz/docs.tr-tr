---
title: 3503 - DuplicateCorrelationQuery
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 60367b33e1e57cce8646b4fcde79c7d4fd20a4cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="540c8-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="540c8-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="540c8-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="540c8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="540c8-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="540c8-104">ID</span></span>|<span data-ttu-id="540c8-105">3503</span><span class="sxs-lookup"><span data-stu-id="540c8-105">3503</span></span>|  
|<span data-ttu-id="540c8-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="540c8-106">Keywords</span></span>|<span data-ttu-id="540c8-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="540c8-107">WFServices</span></span>|  
|<span data-ttu-id="540c8-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="540c8-108">Level</span></span>|<span data-ttu-id="540c8-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="540c8-109">Warning</span></span>|  
|<span data-ttu-id="540c8-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="540c8-110">Channel</span></span>|<span data-ttu-id="540c8-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="540c8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="540c8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="540c8-112">Description</span></span>  
 <span data-ttu-id="540c8-113">Yinelenen CorrelationQuery bulundu gösterir.</span><span class="sxs-lookup"><span data-stu-id="540c8-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="540c8-114">Yinelenen sorgu bağıntı hesaplanırken kullanılmayacak.</span><span class="sxs-lookup"><span data-stu-id="540c8-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="540c8-115">İleti</span><span class="sxs-lookup"><span data-stu-id="540c8-115">Message</span></span>  
 <span data-ttu-id="540c8-116">Yinelenen CorrelationQuery bulunduğu yerle bulundu = '%1'.</span><span class="sxs-lookup"><span data-stu-id="540c8-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="540c8-117">Bu yinelenen sorgu bağıntı hesaplanırken kullanılmayacak.</span><span class="sxs-lookup"><span data-stu-id="540c8-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="540c8-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="540c8-118">Details</span></span>  
  
|<span data-ttu-id="540c8-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="540c8-119">Data Item Name</span></span>|<span data-ttu-id="540c8-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="540c8-120">Data Item Type</span></span>|<span data-ttu-id="540c8-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="540c8-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="540c8-122">Where</span><span class="sxs-lookup"><span data-stu-id="540c8-122">Where</span></span>|<span data-ttu-id="540c8-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="540c8-123">xs:string</span></span>|<span data-ttu-id="540c8-124">Where bağıntı sorgu kısmı.</span><span class="sxs-lookup"><span data-stu-id="540c8-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="540c8-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="540c8-125">AppDomain</span></span>|<span data-ttu-id="540c8-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="540c8-126">xs:string</span></span>|<span data-ttu-id="540c8-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="540c8-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
