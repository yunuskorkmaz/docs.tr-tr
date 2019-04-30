---
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 83f39be84a8d62962b85652b0e39b537c92e612c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781777"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="54e03-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="54e03-102">218 - ClientOperationCompleted</span></span>
## <a name="properties"></a><span data-ttu-id="54e03-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="54e03-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="54e03-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="54e03-104">ID</span></span>|<span data-ttu-id="54e03-105">218</span><span class="sxs-lookup"><span data-stu-id="54e03-105">218</span></span>|  
|<span data-ttu-id="54e03-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="54e03-106">Keywords</span></span>|<span data-ttu-id="54e03-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="54e03-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="54e03-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="54e03-108">Level</span></span>|<span data-ttu-id="54e03-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="54e03-109">Information</span></span>|  
|<span data-ttu-id="54e03-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="54e03-110">Channel</span></span>|<span data-ttu-id="54e03-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="54e03-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="54e03-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54e03-112">Description</span></span>  
 <span data-ttu-id="54e03-113">Bu olay, yalnızca bir işlem tamamlandıktan sonra istemciler tarafından yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="54e03-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="54e03-114">Yalnızca ileti başarıyla gönderildiğinde tek yönlü işlemlerinde budur.</span><span class="sxs-lookup"><span data-stu-id="54e03-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="54e03-115">Yanıt alındıktan sonra istek yanıt işlemlerinde budur.</span><span class="sxs-lookup"><span data-stu-id="54e03-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="54e03-116">İleti</span><span class="sxs-lookup"><span data-stu-id="54e03-116">Message</span></span>  
 <span data-ttu-id="54e03-117">İstemci, '%2' Sözleşmesi ile ilişkilendirilmiş ' %1' eylemi yürütülürken tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="54e03-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="54e03-118">'%3' iletisi gönderildi.</span><span class="sxs-lookup"><span data-stu-id="54e03-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="54e03-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="54e03-119">Details</span></span>  
  
|<span data-ttu-id="54e03-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="54e03-120">Data Item Name</span></span>|<span data-ttu-id="54e03-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="54e03-121">Data Item Type</span></span>|<span data-ttu-id="54e03-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54e03-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="54e03-123">Eylem</span><span class="sxs-lookup"><span data-stu-id="54e03-123">Action</span></span>|<span data-ttu-id="54e03-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="54e03-124">xs:string</span></span>|<span data-ttu-id="54e03-125">Giden iletinin SOAP eylemi üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="54e03-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="54e03-126">Sözleşme adı</span><span class="sxs-lookup"><span data-stu-id="54e03-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="54e03-127">Sözleşme adı.</span><span class="sxs-lookup"><span data-stu-id="54e03-127">The name of the contract.</span></span> <span data-ttu-id="54e03-128">Örnek: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="54e03-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="54e03-129">Hedef</span><span class="sxs-lookup"><span data-stu-id="54e03-129">Destination</span></span>|`xs:string`|<span data-ttu-id="54e03-130">İletinin gönderildiği hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="54e03-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="54e03-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="54e03-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="54e03-132">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="54e03-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="54e03-133">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="54e03-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="54e03-134">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="54e03-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="54e03-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="54e03-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="54e03-136">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="54e03-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
