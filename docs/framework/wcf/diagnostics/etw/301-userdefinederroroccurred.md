---
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 6eb80d6f0b20af9aae6e7de5248323088e352b26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596485"
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="77a91-102">301 - UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="77a91-102">301 - UserDefinedErrorOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="77a91-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="77a91-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="77a91-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="77a91-104">ID</span></span>|<span data-ttu-id="77a91-105">301</span><span class="sxs-lookup"><span data-stu-id="77a91-105">301</span></span>|  
|<span data-ttu-id="77a91-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="77a91-106">Keywords</span></span>|<span data-ttu-id="77a91-107">Sorun giderme, ögesi, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="77a91-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="77a91-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="77a91-108">Level</span></span>|<span data-ttu-id="77a91-109">Hata</span><span class="sxs-lookup"><span data-stu-id="77a91-109">Error</span></span>|  
|<span data-ttu-id="77a91-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="77a91-110">Channel</span></span>|<span data-ttu-id="77a91-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="77a91-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="77a91-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77a91-112">Description</span></span>  
 <span data-ttu-id="77a91-113">Bu olay kullanıcı kodundan yayılır.</span><span class="sxs-lookup"><span data-stu-id="77a91-113">This event is emitted from user code.</span></span> <span data-ttu-id="77a91-114">Geliştiriciler kendi hizmetinde özel tanımlı bir hata oluştuğunda bu olay gönderebilir.</span><span class="sxs-lookup"><span data-stu-id="77a91-114">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="77a91-115">Bu yapılabilir kullanarak <xref:System.Diagnostics.Eventing> API'leri.</span><span class="sxs-lookup"><span data-stu-id="77a91-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="77a91-116">Ayrıca, bu API sarmalar ve bu olay düzgün bir şekilde yayma yapmayı gösteren bir WCF örnek yok.</span><span class="sxs-lookup"><span data-stu-id="77a91-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="77a91-117">İleti</span><span class="sxs-lookup"><span data-stu-id="77a91-117">Message</span></span>  
 <span data-ttu-id="77a91-118">Ad: '%1', başvuru: '%2', yükü: % 3</span><span class="sxs-lookup"><span data-stu-id="77a91-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="77a91-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="77a91-119">Details</span></span>  
  
|<span data-ttu-id="77a91-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="77a91-120">Data Item Name</span></span>|<span data-ttu-id="77a91-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="77a91-121">Data Item Type</span></span>|<span data-ttu-id="77a91-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77a91-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="77a91-123">Ad</span><span class="sxs-lookup"><span data-stu-id="77a91-123">Name</span></span>|`xs:string`|<span data-ttu-id="77a91-124">Kullanıcı tanımlı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="77a91-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="77a91-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="77a91-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="77a91-126">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77a91-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="77a91-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="77a91-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="77a91-128">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="77a91-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="77a91-129">Yükü</span><span class="sxs-lookup"><span data-stu-id="77a91-129">Payload</span></span>|`xs:string`|<span data-ttu-id="77a91-130">Kullanıcı tanımlı yükü olay.</span><span class="sxs-lookup"><span data-stu-id="77a91-130">The user-defined payload of the event.</span></span>|
