---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755590"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="4cd8c-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="4cd8c-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>
## <a name="properties"></a><span data-ttu-id="4cd8c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4cd8c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4cd8c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="4cd8c-104">ID</span></span>|<span data-ttu-id="4cd8c-105">3550</span><span class="sxs-lookup"><span data-stu-id="4cd8c-105">3550</span></span>|  
|<span data-ttu-id="4cd8c-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4cd8c-106">Keywords</span></span>|<span data-ttu-id="4cd8c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="4cd8c-107">WFServices</span></span>|  
|<span data-ttu-id="4cd8c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4cd8c-108">Level</span></span>|<span data-ttu-id="4cd8c-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="4cd8c-109">Information</span></span>|  
|<span data-ttu-id="4cd8c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4cd8c-110">Channel</span></span>|<span data-ttu-id="4cd8c-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="4cd8c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4cd8c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cd8c-112">Description</span></span>  
 <span data-ttu-id="4cd8c-113">Arabelleğe alınmış alma işlemi başarısız oldu gösterir.</span><span class="sxs-lookup"><span data-stu-id="4cd8c-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="4cd8c-114">Hizmet örneği bu belirli bir işlemi hazır olduğunda işlem yeniden denenecek.</span><span class="sxs-lookup"><span data-stu-id="4cd8c-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4cd8c-115">İleti</span><span class="sxs-lookup"><span data-stu-id="4cd8c-115">Message</span></span>  
 <span data-ttu-id="4cd8c-116">'%1' işlemi şu anda gerçekleştirilemiyor.</span><span class="sxs-lookup"><span data-stu-id="4cd8c-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="4cd8c-117">Hizmet örneği bu belirli bir işlemi hazır olduğunda başka bir deneme yapılır.</span><span class="sxs-lookup"><span data-stu-id="4cd8c-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4cd8c-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4cd8c-118">Details</span></span>  
  
|<span data-ttu-id="4cd8c-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4cd8c-119">Data Item Name</span></span>|<span data-ttu-id="4cd8c-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4cd8c-120">Data Item Type</span></span>|<span data-ttu-id="4cd8c-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4cd8c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4cd8c-122">OperationName</span><span class="sxs-lookup"><span data-stu-id="4cd8c-122">OperationName</span></span>|<span data-ttu-id="4cd8c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="4cd8c-123">xs:string</span></span>|<span data-ttu-id="4cd8c-124">İşlemin adı.</span><span class="sxs-lookup"><span data-stu-id="4cd8c-124">The name of the operation.</span></span>|  
|<span data-ttu-id="4cd8c-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4cd8c-125">AppDomain</span></span>|<span data-ttu-id="4cd8c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="4cd8c-126">xs:string</span></span>|<span data-ttu-id="4cd8c-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4cd8c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
