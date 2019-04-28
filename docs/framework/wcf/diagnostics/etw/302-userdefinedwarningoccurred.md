---
title: 302 - UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: c70857951309ef54ba460e96e948c9320269d30f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596758"
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="ad5b5-102">302 - UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="ad5b5-102">302 - UserDefinedWarningOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="ad5b5-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ad5b5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad5b5-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ad5b5-104">ID</span></span>|<span data-ttu-id="ad5b5-105">302</span><span class="sxs-lookup"><span data-stu-id="ad5b5-105">302</span></span>|  
|<span data-ttu-id="ad5b5-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ad5b5-106">Keywords</span></span>|<span data-ttu-id="ad5b5-107">Sorun giderme, ögesi, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="ad5b5-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="ad5b5-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ad5b5-108">Level</span></span>|<span data-ttu-id="ad5b5-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="ad5b5-109">Warning</span></span>|  
|<span data-ttu-id="ad5b5-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ad5b5-110">Channel</span></span>|<span data-ttu-id="ad5b5-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ad5b5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ad5b5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad5b5-112">Description</span></span>  
 <span data-ttu-id="ad5b5-113">Bu olay kullanıcı kodundan yayılır.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-113">This event is emitted from user code.</span></span> <span data-ttu-id="ad5b5-114">Geliştiriciler kendi hizmetinde özel tanımlı uyarı olayı ortaya çıktığında bu olay gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="ad5b5-115">Bu yapılabilir kullanarak <xref:System.Diagnostics.Eventing> API'leri.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="ad5b5-116">Ayrıca, bu API sarmalar ve bu olay düzgün bir şekilde yayma yapmayı gösteren bir WCF örnek yok.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ad5b5-117">İleti</span><span class="sxs-lookup"><span data-stu-id="ad5b5-117">Message</span></span>  
 <span data-ttu-id="ad5b5-118">Ad: '%1', başvuru: '%2', yükü: % 3</span><span class="sxs-lookup"><span data-stu-id="ad5b5-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="ad5b5-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ad5b5-119">Details</span></span>  
  
|<span data-ttu-id="ad5b5-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ad5b5-120">Data Item Name</span></span>|<span data-ttu-id="ad5b5-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ad5b5-121">Data Item Type</span></span>|<span data-ttu-id="ad5b5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ad5b5-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ad5b5-123">Ad</span><span class="sxs-lookup"><span data-stu-id="ad5b5-123">Name</span></span>|`xs:string`|<span data-ttu-id="ad5b5-124">Kullanıcı tanımlı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="ad5b5-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="ad5b5-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="ad5b5-126">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ad5b5-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ad5b5-128">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ad5b5-129">Yükü</span><span class="sxs-lookup"><span data-stu-id="ad5b5-129">Payload</span></span>|`xs:string`|<span data-ttu-id="ad5b5-130">Kullanıcı tanımlı yükü olay.</span><span class="sxs-lookup"><span data-stu-id="ad5b5-130">The user-defined payload of the event.</span></span>|
