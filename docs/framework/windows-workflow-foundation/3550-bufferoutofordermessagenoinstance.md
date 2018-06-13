---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511608"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="23371-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="23371-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="23371-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="23371-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="23371-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="23371-104">ID</span></span>|<span data-ttu-id="23371-105">3550</span><span class="sxs-lookup"><span data-stu-id="23371-105">3550</span></span>|  
|<span data-ttu-id="23371-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="23371-106">Keywords</span></span>|<span data-ttu-id="23371-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="23371-107">WFServices</span></span>|  
|<span data-ttu-id="23371-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="23371-108">Level</span></span>|<span data-ttu-id="23371-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="23371-109">Information</span></span>|  
|<span data-ttu-id="23371-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="23371-110">Channel</span></span>|<span data-ttu-id="23371-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="23371-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="23371-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23371-112">Description</span></span>  
 <span data-ttu-id="23371-113">Arabellekli alma başarısız oldu gösterir.</span><span class="sxs-lookup"><span data-stu-id="23371-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="23371-114">Hizmet örneği belirli bu işlemi hazır olduğunda işlem yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="23371-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="23371-115">İleti</span><span class="sxs-lookup"><span data-stu-id="23371-115">Message</span></span>  
 <span data-ttu-id="23371-116">'%1' işlemi şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="23371-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="23371-117">Hizmet örneği belirli bu işlemi için hazır olduğunda, başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="23371-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="23371-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="23371-118">Details</span></span>  
  
|<span data-ttu-id="23371-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="23371-119">Data Item Name</span></span>|<span data-ttu-id="23371-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="23371-120">Data Item Type</span></span>|<span data-ttu-id="23371-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="23371-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="23371-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="23371-122">OperationName</span></span>|<span data-ttu-id="23371-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="23371-123">xs:string</span></span>|<span data-ttu-id="23371-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="23371-124">The name of the operation.</span></span>|  
|<span data-ttu-id="23371-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="23371-125">AppDomain</span></span>|<span data-ttu-id="23371-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="23371-126">xs:string</span></span>|<span data-ttu-id="23371-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="23371-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
