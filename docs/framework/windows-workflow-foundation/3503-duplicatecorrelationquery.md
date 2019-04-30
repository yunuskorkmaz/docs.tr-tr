---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755603"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="e39e7-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="e39e7-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="e39e7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e39e7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e39e7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e39e7-104">ID</span></span>|<span data-ttu-id="e39e7-105">3503</span><span class="sxs-lookup"><span data-stu-id="e39e7-105">3503</span></span>|  
|<span data-ttu-id="e39e7-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e39e7-106">Keywords</span></span>|<span data-ttu-id="e39e7-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="e39e7-107">WFServices</span></span>|  
|<span data-ttu-id="e39e7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e39e7-108">Level</span></span>|<span data-ttu-id="e39e7-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="e39e7-109">Warning</span></span>|  
|<span data-ttu-id="e39e7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e39e7-110">Channel</span></span>|<span data-ttu-id="e39e7-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="e39e7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e39e7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e39e7-112">Description</span></span>  
 <span data-ttu-id="e39e7-113">Yinelenen CorrelationQuery bulundu belirtir.</span><span class="sxs-lookup"><span data-stu-id="e39e7-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="e39e7-114">Yinelenen sorgu bağıntı hesaplarken kullanılmayacak.</span><span class="sxs-lookup"><span data-stu-id="e39e7-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e39e7-115">İleti</span><span class="sxs-lookup"><span data-stu-id="e39e7-115">Message</span></span>  
 <span data-ttu-id="e39e7-116">Yinelenen CorrelationQuery bulunduğu yerle bulundu = '%1'.</span><span class="sxs-lookup"><span data-stu-id="e39e7-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="e39e7-117">Bu yinelenen bir sorgu bağıntı hesaplarken kullanılmayacak.</span><span class="sxs-lookup"><span data-stu-id="e39e7-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e39e7-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e39e7-118">Details</span></span>  
  
|<span data-ttu-id="e39e7-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e39e7-119">Data Item Name</span></span>|<span data-ttu-id="e39e7-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e39e7-120">Data Item Type</span></span>|<span data-ttu-id="e39e7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e39e7-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e39e7-122">Where</span><span class="sxs-lookup"><span data-stu-id="e39e7-122">Where</span></span>|<span data-ttu-id="e39e7-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="e39e7-123">xs:string</span></span>|<span data-ttu-id="e39e7-124">Where kısmı bağıntı sorgu.</span><span class="sxs-lookup"><span data-stu-id="e39e7-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="e39e7-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e39e7-125">AppDomain</span></span>|<span data-ttu-id="e39e7-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="e39e7-126">xs:string</span></span>|<span data-ttu-id="e39e7-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e39e7-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
