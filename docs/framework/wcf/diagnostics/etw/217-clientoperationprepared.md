---
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: 5979cd8ffe0e05b61af01d2aa98c4a2c63fd432c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461071"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="e070c-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="e070c-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="e070c-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e070c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e070c-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e070c-104">ID</span></span>|<span data-ttu-id="e070c-105">217</span><span class="sxs-lookup"><span data-stu-id="e070c-105">217</span></span>|  
|<span data-ttu-id="e070c-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e070c-106">Keywords</span></span>|<span data-ttu-id="e070c-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e070c-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e070c-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e070c-108">Level</span></span>|<span data-ttu-id="e070c-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="e070c-109">Information</span></span>|  
|<span data-ttu-id="e070c-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e070c-110">Channel</span></span>|<span data-ttu-id="e070c-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="e070c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e070c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e070c-112">Description</span></span>  
 <span data-ttu-id="e070c-113">Bu olay yalnızca bir işlem hizmetine gönderilmeden önce istemcileri tarafından yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="e070c-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e070c-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e070c-114">Message</span></span>  
 <span data-ttu-id="e070c-115">İstemci, '%2' sözleşmeyle ilişkilendirilmiş ' %1' eylemi yürütüyor.</span><span class="sxs-lookup"><span data-stu-id="e070c-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="e070c-116">'%3' ileti gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e070c-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e070c-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e070c-117">Details</span></span>  
  
|<span data-ttu-id="e070c-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e070c-118">Data Item Name</span></span>|<span data-ttu-id="e070c-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e070c-119">Data Item Type</span></span>|<span data-ttu-id="e070c-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e070c-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e070c-121">Eylem</span><span class="sxs-lookup"><span data-stu-id="e070c-121">Action</span></span>|`xs:string`|<span data-ttu-id="e070c-122">Giden iletinin SOAP eylemi üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="e070c-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="e070c-123">Sözleşme adı</span><span class="sxs-lookup"><span data-stu-id="e070c-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="e070c-124">Anlaşma adı.</span><span class="sxs-lookup"><span data-stu-id="e070c-124">The name of the contract.</span></span> <span data-ttu-id="e070c-125">Örnek: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="e070c-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="e070c-126">Hedef</span><span class="sxs-lookup"><span data-stu-id="e070c-126">Destination</span></span>|`xs:string`|<span data-ttu-id="e070c-127">İleti gönderilir hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="e070c-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="e070c-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="e070c-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="e070c-129">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e070c-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e070c-130">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="e070c-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e070c-131">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="e070c-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e070c-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e070c-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e070c-133">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e070c-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
