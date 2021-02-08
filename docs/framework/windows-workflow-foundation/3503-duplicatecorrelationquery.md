---
description: 'Hakkında daha fazla bilgi edinin: 3503-DuplicateCorrelationQuery'
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: a8e1e41aad3aa1b273d8f8a5d7b0768fabe4e658
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778080"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="f53ad-103">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="f53ad-103">3503 - DuplicateCorrelationQuery</span></span>

## <a name="properties"></a><span data-ttu-id="f53ad-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f53ad-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f53ad-105">ID</span><span class="sxs-lookup"><span data-stu-id="f53ad-105">ID</span></span>|<span data-ttu-id="f53ad-106">3503</span><span class="sxs-lookup"><span data-stu-id="f53ad-106">3503</span></span>|  
|<span data-ttu-id="f53ad-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f53ad-107">Keywords</span></span>|<span data-ttu-id="f53ad-108">WFServices</span><span class="sxs-lookup"><span data-stu-id="f53ad-108">WFServices</span></span>|  
|<span data-ttu-id="f53ad-109">Level</span><span class="sxs-lookup"><span data-stu-id="f53ad-109">Level</span></span>|<span data-ttu-id="f53ad-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="f53ad-110">Warning</span></span>|  
|<span data-ttu-id="f53ad-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="f53ad-111">Channel</span></span>|<span data-ttu-id="f53ad-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="f53ad-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f53ad-113">Description</span><span class="sxs-lookup"><span data-stu-id="f53ad-113">Description</span></span>  

 <span data-ttu-id="f53ad-114">Yinelenen bir CorrelationQuery bulundu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f53ad-114">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="f53ad-115">Bağıntı hesaplanırken yinelenen sorgu kullanılmayacak.</span><span class="sxs-lookup"><span data-stu-id="f53ad-115">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f53ad-116">İleti</span><span class="sxs-lookup"><span data-stu-id="f53ad-116">Message</span></span>  

 <span data-ttu-id="f53ad-117">Burada = ' %1 ' olan yinelenen bir CorrelationQuery bulundu.</span><span class="sxs-lookup"><span data-stu-id="f53ad-117">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="f53ad-118">Bu yinelenen sorgu, bağıntı hesaplanırken kullanılmayacak.</span><span class="sxs-lookup"><span data-stu-id="f53ad-118">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f53ad-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f53ad-119">Details</span></span>  
  
|<span data-ttu-id="f53ad-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f53ad-120">Data Item Name</span></span>|<span data-ttu-id="f53ad-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f53ad-121">Data Item Type</span></span>|<span data-ttu-id="f53ad-122">Description</span><span class="sxs-lookup"><span data-stu-id="f53ad-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f53ad-123">Konum</span><span class="sxs-lookup"><span data-stu-id="f53ad-123">Where</span></span>|<span data-ttu-id="f53ad-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="f53ad-124">xs:string</span></span>|<span data-ttu-id="f53ad-125">Bağıntı sorgusunun WHERE kısmı.</span><span class="sxs-lookup"><span data-stu-id="f53ad-125">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="f53ad-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f53ad-126">AppDomain</span></span>|<span data-ttu-id="f53ad-127">xs: String</span><span class="sxs-lookup"><span data-stu-id="f53ad-127">xs:string</span></span>|<span data-ttu-id="f53ad-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f53ad-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
