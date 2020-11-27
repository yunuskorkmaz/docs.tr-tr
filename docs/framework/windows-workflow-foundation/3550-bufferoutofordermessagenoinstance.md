---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 61605d666911cce277bcebbb0a2f803e9a5dcfeb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261312"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="2a7f4-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="2a7f4-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>

## <a name="properties"></a><span data-ttu-id="2a7f4-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2a7f4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a7f4-104">ID</span><span class="sxs-lookup"><span data-stu-id="2a7f4-104">ID</span></span>|<span data-ttu-id="2a7f4-105">3550</span><span class="sxs-lookup"><span data-stu-id="2a7f4-105">3550</span></span>|  
|<span data-ttu-id="2a7f4-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="2a7f4-106">Keywords</span></span>|<span data-ttu-id="2a7f4-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="2a7f4-107">WFServices</span></span>|  
|<span data-ttu-id="2a7f4-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="2a7f4-108">Level</span></span>|<span data-ttu-id="2a7f4-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="2a7f4-109">Information</span></span>|  
|<span data-ttu-id="2a7f4-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="2a7f4-110">Channel</span></span>|<span data-ttu-id="2a7f4-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="2a7f4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2a7f4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a7f4-112">Description</span></span>  

 <span data-ttu-id="2a7f4-113">Arabelleğe alınan bir alma başarısız olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a7f4-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="2a7f4-114">Hizmet örneği bu belirli işlemi işlemeye hazırsa işlem yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="2a7f4-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2a7f4-115">İleti</span><span class="sxs-lookup"><span data-stu-id="2a7f4-115">Message</span></span>  

 <span data-ttu-id="2a7f4-116">' %1 ' işlemi şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="2a7f4-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="2a7f4-117">Hizmet örneği bu işlemi işlemeye hazırsa başka bir girişim yapılacak.</span><span class="sxs-lookup"><span data-stu-id="2a7f4-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2a7f4-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2a7f4-118">Details</span></span>  
  
|<span data-ttu-id="2a7f4-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2a7f4-119">Data Item Name</span></span>|<span data-ttu-id="2a7f4-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2a7f4-120">Data Item Type</span></span>|<span data-ttu-id="2a7f4-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a7f4-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2a7f4-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="2a7f4-122">OperationName</span></span>|<span data-ttu-id="2a7f4-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="2a7f4-123">xs:string</span></span>|<span data-ttu-id="2a7f4-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="2a7f4-124">The name of the operation.</span></span>|  
|<span data-ttu-id="2a7f4-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2a7f4-125">AppDomain</span></span>|<span data-ttu-id="2a7f4-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="2a7f4-126">xs:string</span></span>|<span data-ttu-id="2a7f4-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2a7f4-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
