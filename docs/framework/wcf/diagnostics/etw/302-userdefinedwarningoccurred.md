---
title: 302 - UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: b942b2e9716713371b8679fc9df9b9634dfc7283
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96243449"
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="10a17-102">302 - UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="10a17-102">302 - UserDefinedWarningOccurred</span></span>

## <a name="properties"></a><span data-ttu-id="10a17-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="10a17-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10a17-104">ID</span><span class="sxs-lookup"><span data-stu-id="10a17-104">ID</span></span>|<span data-ttu-id="10a17-105">302</span><span class="sxs-lookup"><span data-stu-id="10a17-105">302</span></span>|  
|<span data-ttu-id="10a17-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="10a17-106">Keywords</span></span>|<span data-ttu-id="10a17-107">Sorun giderme, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="10a17-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="10a17-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="10a17-108">Level</span></span>|<span data-ttu-id="10a17-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="10a17-109">Warning</span></span>|  
|<span data-ttu-id="10a17-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="10a17-110">Channel</span></span>|<span data-ttu-id="10a17-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="10a17-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="10a17-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10a17-112">Description</span></span>  

 <span data-ttu-id="10a17-113">Bu olay kullanıcı kodundan yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="10a17-113">This event is emitted from user code.</span></span> <span data-ttu-id="10a17-114">Geliştiriciler, hizmetinde özel tanımlanmış bir uyarı olayı oluştuğunda bu olayı oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="10a17-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="10a17-115">Bu, API 'ler kullanılarak yapılabilir <xref:System.Diagnostics.Eventing> .</span><span class="sxs-lookup"><span data-stu-id="10a17-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="10a17-116">Ayrıca, bu API 'YI sarmalayan ve bu olayı doğru şekilde nasıl yayılacağını gösteren bir WCF örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="10a17-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="10a17-117">İleti</span><span class="sxs-lookup"><span data-stu-id="10a17-117">Message</span></span>  

 <span data-ttu-id="10a17-118">Ad: ' %1 ', başvuru: ' %2 ', yük: %3</span><span class="sxs-lookup"><span data-stu-id="10a17-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="10a17-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="10a17-119">Details</span></span>  
  
|<span data-ttu-id="10a17-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="10a17-120">Data Item Name</span></span>|<span data-ttu-id="10a17-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="10a17-121">Data Item Type</span></span>|<span data-ttu-id="10a17-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="10a17-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="10a17-123">Ad</span><span class="sxs-lookup"><span data-stu-id="10a17-123">Name</span></span>|`xs:string`|<span data-ttu-id="10a17-124">Etkinliğin Kullanıcı tanımlı adı.</span><span class="sxs-lookup"><span data-stu-id="10a17-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="10a17-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="10a17-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="10a17-126">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="10a17-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="10a17-127">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="10a17-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="10a17-128">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="10a17-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="10a17-129">Te</span><span class="sxs-lookup"><span data-stu-id="10a17-129">Payload</span></span>|`xs:string`|<span data-ttu-id="10a17-130">Etkinliğin Kullanıcı tanımlı yükü.</span><span class="sxs-lookup"><span data-stu-id="10a17-130">The user-defined payload of the event.</span></span>|
