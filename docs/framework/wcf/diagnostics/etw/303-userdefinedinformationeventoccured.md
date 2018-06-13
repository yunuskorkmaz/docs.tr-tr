---
title: 303 - UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 0b782b5ac0527b5acb3ebf0bf11c117563042495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459146"
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="c74b7-102">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="c74b7-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="c74b7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c74b7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c74b7-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c74b7-104">ID</span></span>|<span data-ttu-id="c74b7-105">303</span><span class="sxs-lookup"><span data-stu-id="c74b7-105">303</span></span>|  
|<span data-ttu-id="c74b7-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c74b7-106">Keywords</span></span>|<span data-ttu-id="c74b7-107">Sorun giderme, ögesi, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="c74b7-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="c74b7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c74b7-108">Level</span></span>|<span data-ttu-id="c74b7-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="c74b7-109">Information</span></span>|  
|<span data-ttu-id="c74b7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c74b7-110">Channel</span></span>|<span data-ttu-id="c74b7-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="c74b7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c74b7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c74b7-112">Description</span></span>  
 <span data-ttu-id="c74b7-113">Bu olay, kullanıcı kodundan yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="c74b7-113">This event is emitted from user code.</span></span> <span data-ttu-id="c74b7-114">Geliştiriciler kendi hizmetinde özel tanımlı bilgilendirici olay ortaya çıktığında bu olay yayma.</span><span class="sxs-lookup"><span data-stu-id="c74b7-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="c74b7-115">Bu yapılabilir kullanarak <xref:System.Diagnostics.Eventing> API'leri.</span><span class="sxs-lookup"><span data-stu-id="c74b7-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="c74b7-116">Ayrıca, bu API sarmalar ve bu olay düzgün bir şekilde yayma yapmayı gösteren bir WCF örneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="c74b7-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c74b7-117">İleti</span><span class="sxs-lookup"><span data-stu-id="c74b7-117">Message</span></span>  
 <span data-ttu-id="c74b7-118">Ad: '%1', başvuru: '%2', yük: % 3</span><span class="sxs-lookup"><span data-stu-id="c74b7-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="c74b7-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c74b7-119">Details</span></span>  
  
|<span data-ttu-id="c74b7-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c74b7-120">Data Item Name</span></span>|<span data-ttu-id="c74b7-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c74b7-121">Data Item Type</span></span>|<span data-ttu-id="c74b7-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c74b7-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c74b7-123">Ad</span><span class="sxs-lookup"><span data-stu-id="c74b7-123">Name</span></span>|`xs:string`|<span data-ttu-id="c74b7-124">Olayın kullanıcı tanımlı adı</span><span class="sxs-lookup"><span data-stu-id="c74b7-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="c74b7-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="c74b7-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="c74b7-126">Bu alan, barındırılan Web Hizmetleri için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c74b7-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c74b7-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="c74b7-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c74b7-128">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="c74b7-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c74b7-129">Yükü</span><span class="sxs-lookup"><span data-stu-id="c74b7-129">Payload</span></span>|`xs:string`|<span data-ttu-id="c74b7-130">Kullanıcı tanımlı yükü olay.</span><span class="sxs-lookup"><span data-stu-id="c74b7-130">The user-defined payload of the event.</span></span>|
