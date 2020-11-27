---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: e1e64824ee9a95757ed7c00aa17fa80898219401
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270334"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="037c6-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="037c6-102">3503 - DuplicateCorrelationQuery</span></span>

## <a name="properties"></a><span data-ttu-id="037c6-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="037c6-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="037c6-104">ID</span><span class="sxs-lookup"><span data-stu-id="037c6-104">ID</span></span>|<span data-ttu-id="037c6-105">3503</span><span class="sxs-lookup"><span data-stu-id="037c6-105">3503</span></span>|  
|<span data-ttu-id="037c6-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="037c6-106">Keywords</span></span>|<span data-ttu-id="037c6-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="037c6-107">WFServices</span></span>|  
|<span data-ttu-id="037c6-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="037c6-108">Level</span></span>|<span data-ttu-id="037c6-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="037c6-109">Warning</span></span>|  
|<span data-ttu-id="037c6-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="037c6-110">Channel</span></span>|<span data-ttu-id="037c6-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="037c6-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="037c6-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="037c6-112">Description</span></span>  

 <span data-ttu-id="037c6-113">Yinelenen bir CorrelationQuery bulundu olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="037c6-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="037c6-114">Bağıntı hesaplanırken yinelenen sorgu kullanılmayacak.</span><span class="sxs-lookup"><span data-stu-id="037c6-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="037c6-115">İleti</span><span class="sxs-lookup"><span data-stu-id="037c6-115">Message</span></span>  

 <span data-ttu-id="037c6-116">Burada = ' %1 ' olan yinelenen bir CorrelationQuery bulundu.</span><span class="sxs-lookup"><span data-stu-id="037c6-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="037c6-117">Bu yinelenen sorgu, bağıntı hesaplanırken kullanılmayacak.</span><span class="sxs-lookup"><span data-stu-id="037c6-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="037c6-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="037c6-118">Details</span></span>  
  
|<span data-ttu-id="037c6-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="037c6-119">Data Item Name</span></span>|<span data-ttu-id="037c6-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="037c6-120">Data Item Type</span></span>|<span data-ttu-id="037c6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="037c6-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="037c6-122">Konum</span><span class="sxs-lookup"><span data-stu-id="037c6-122">Where</span></span>|<span data-ttu-id="037c6-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="037c6-123">xs:string</span></span>|<span data-ttu-id="037c6-124">Bağıntı sorgusunun WHERE kısmı.</span><span class="sxs-lookup"><span data-stu-id="037c6-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="037c6-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="037c6-125">AppDomain</span></span>|<span data-ttu-id="037c6-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="037c6-126">xs:string</span></span>|<span data-ttu-id="037c6-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="037c6-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
