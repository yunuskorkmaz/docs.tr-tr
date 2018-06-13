---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: 37a689b30b0bcab9124472deb98627afbe30dfee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511406"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="ea055-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="ea055-102">3503 - DuplicateCorrelationQuery</span></span>
## <a name="properties"></a><span data-ttu-id="ea055-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ea055-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ea055-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ea055-104">ID</span></span>|<span data-ttu-id="ea055-105">3503</span><span class="sxs-lookup"><span data-stu-id="ea055-105">3503</span></span>|  
|<span data-ttu-id="ea055-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ea055-106">Keywords</span></span>|<span data-ttu-id="ea055-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="ea055-107">WFServices</span></span>|  
|<span data-ttu-id="ea055-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ea055-108">Level</span></span>|<span data-ttu-id="ea055-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="ea055-109">Warning</span></span>|  
|<span data-ttu-id="ea055-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ea055-110">Channel</span></span>|<span data-ttu-id="ea055-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ea055-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ea055-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea055-112">Description</span></span>  
 <span data-ttu-id="ea055-113">Yinelenen CorrelationQuery bulundu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ea055-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="ea055-114">Yinelenen sorgu bağıntı hesaplanırken kullanılmayacak.</span><span class="sxs-lookup"><span data-stu-id="ea055-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ea055-115">İleti</span><span class="sxs-lookup"><span data-stu-id="ea055-115">Message</span></span>  
 <span data-ttu-id="ea055-116">Yinelenen CorrelationQuery bulunduğu yerle bulundu = '%1'.</span><span class="sxs-lookup"><span data-stu-id="ea055-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="ea055-117">Bu yinelenen sorgu bağıntı hesaplanırken kullanılmayacak.</span><span class="sxs-lookup"><span data-stu-id="ea055-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ea055-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ea055-118">Details</span></span>  
  
|<span data-ttu-id="ea055-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ea055-119">Data Item Name</span></span>|<span data-ttu-id="ea055-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ea055-120">Data Item Type</span></span>|<span data-ttu-id="ea055-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea055-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ea055-122">Where</span><span class="sxs-lookup"><span data-stu-id="ea055-122">Where</span></span>|<span data-ttu-id="ea055-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="ea055-123">xs:string</span></span>|<span data-ttu-id="ea055-124">Where bağıntı sorgu kısmı.</span><span class="sxs-lookup"><span data-stu-id="ea055-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="ea055-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ea055-125">AppDomain</span></span>|<span data-ttu-id="ea055-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="ea055-126">xs:string</span></span>|<span data-ttu-id="ea055-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ea055-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
