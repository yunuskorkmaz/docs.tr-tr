---
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457980"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="1aee9-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="1aee9-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="1aee9-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1aee9-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1aee9-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="1aee9-104">ID</span></span>|<span data-ttu-id="1aee9-105">218</span><span class="sxs-lookup"><span data-stu-id="1aee9-105">218</span></span>|  
|<span data-ttu-id="1aee9-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="1aee9-106">Keywords</span></span>|<span data-ttu-id="1aee9-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1aee9-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="1aee9-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1aee9-108">Level</span></span>|<span data-ttu-id="1aee9-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="1aee9-109">Information</span></span>|  
|<span data-ttu-id="1aee9-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1aee9-110">Channel</span></span>|<span data-ttu-id="1aee9-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="1aee9-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1aee9-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1aee9-112">Description</span></span>  
 <span data-ttu-id="1aee9-113">Bu olay yalnızca bir işlem tamamlandıktan sonra istemciler tarafından yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="1aee9-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="1aee9-114">Yalnızca ileti başarıyla gönderildikten sonra tek yönlü işlemlerinde budur.</span><span class="sxs-lookup"><span data-stu-id="1aee9-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="1aee9-115">Yanıt alındıktan sonra istek-yanıt işlemlerinde budur.</span><span class="sxs-lookup"><span data-stu-id="1aee9-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1aee9-116">İleti</span><span class="sxs-lookup"><span data-stu-id="1aee9-116">Message</span></span>  
 <span data-ttu-id="1aee9-117">İstemci, '%2' sözleşmeyle ilişkilendirilmiş ' %1' eylemi yürütülürken tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="1aee9-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="1aee9-118">'%3' ileti gönderildi.</span><span class="sxs-lookup"><span data-stu-id="1aee9-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1aee9-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1aee9-119">Details</span></span>  
  
|<span data-ttu-id="1aee9-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1aee9-120">Data Item Name</span></span>|<span data-ttu-id="1aee9-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1aee9-121">Data Item Type</span></span>|<span data-ttu-id="1aee9-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1aee9-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1aee9-123">Eylem</span><span class="sxs-lookup"><span data-stu-id="1aee9-123">Action</span></span>|<span data-ttu-id="1aee9-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="1aee9-124">xs:string</span></span>|<span data-ttu-id="1aee9-125">Giden iletinin SOAP eylemi üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="1aee9-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="1aee9-126">Sözleşme adı</span><span class="sxs-lookup"><span data-stu-id="1aee9-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="1aee9-127">Anlaşma adı.</span><span class="sxs-lookup"><span data-stu-id="1aee9-127">The name of the contract.</span></span> <span data-ttu-id="1aee9-128">Örnek: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="1aee9-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="1aee9-129">Hedef</span><span class="sxs-lookup"><span data-stu-id="1aee9-129">Destination</span></span>|`xs:string`|<span data-ttu-id="1aee9-130">İletinin gönderildiği hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="1aee9-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="1aee9-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="1aee9-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="1aee9-132">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1aee9-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1aee9-133">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="1aee9-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1aee9-134">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="1aee9-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1aee9-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1aee9-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1aee9-136">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1aee9-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
