---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781842"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="91b17-102">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="91b17-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="91b17-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="91b17-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="91b17-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="91b17-104">ID</span></span>|<span data-ttu-id="91b17-105">215</span><span class="sxs-lookup"><span data-stu-id="91b17-105">215</span></span>|  
|<span data-ttu-id="91b17-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="91b17-106">Keywords</span></span>|<span data-ttu-id="91b17-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="91b17-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="91b17-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="91b17-108">Level</span></span>|<span data-ttu-id="91b17-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="91b17-109">Information</span></span>|  
|<span data-ttu-id="91b17-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="91b17-110">Channel</span></span>|<span data-ttu-id="91b17-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="91b17-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="91b17-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91b17-112">Description</span></span>  
 <span data-ttu-id="91b17-113">Bu olay bir TCP tabanlı taşıma bir ileti aldığında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="91b17-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="91b17-114">Not taşıma düzeyinde birden çok ileti istemcileri ve Hizmetleri tek bir işlem için arasında değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="91b17-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="91b17-115">Bu altyapı davranışı nedeniyle olabilir, güvenlik iyi bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="91b17-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="91b17-116">Bu nedenle, sayısını `MessageReceivedByTransport` yayılan iş olayları hizmetinizin bağlama ve yapılandırmasına bağlı olarak değişir.</span><span class="sxs-lookup"><span data-stu-id="91b17-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91b17-117">Bu olay için tek yönlü aktarmaları yayılan değil.</span><span class="sxs-lookup"><span data-stu-id="91b17-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="91b17-118">İleti</span><span class="sxs-lookup"><span data-stu-id="91b17-118">Message</span></span>  
 <span data-ttu-id="91b17-119">Taşıma, '%1' den bir ileti alındı.</span><span class="sxs-lookup"><span data-stu-id="91b17-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="91b17-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="91b17-120">Details</span></span>  
  
|<span data-ttu-id="91b17-121">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="91b17-121">Data Item Name</span></span>|<span data-ttu-id="91b17-122">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="91b17-122">Data Item Type</span></span>|<span data-ttu-id="91b17-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91b17-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="91b17-124">Dinleme adresi</span><span class="sxs-lookup"><span data-stu-id="91b17-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="91b17-125">Alınan ileti adresi.</span><span class="sxs-lookup"><span data-stu-id="91b17-125">The address that received the message.</span></span>|  
|<span data-ttu-id="91b17-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="91b17-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="91b17-127">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="91b17-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="91b17-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="91b17-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="91b17-129">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="91b17-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="91b17-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="91b17-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="91b17-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="91b17-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
