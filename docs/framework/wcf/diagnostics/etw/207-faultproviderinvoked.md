---
description: 'Hakkında daha fazla bilgi edinin: 207-Faultproviderçağrılan'
title: 207 - FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 03c4f1669fc61019ccf4d23d2994f136e231fbec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728073"
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="d5d68-103">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="d5d68-103">207 - FaultProviderInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="d5d68-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d5d68-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5d68-105">ID</span><span class="sxs-lookup"><span data-stu-id="d5d68-105">ID</span></span>|<span data-ttu-id="d5d68-106">207</span><span class="sxs-lookup"><span data-stu-id="d5d68-106">207</span></span>|  
|<span data-ttu-id="d5d68-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="d5d68-107">Keywords</span></span>|<span data-ttu-id="d5d68-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d5d68-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d5d68-109">Level</span><span class="sxs-lookup"><span data-stu-id="d5d68-109">Level</span></span>|<span data-ttu-id="d5d68-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="d5d68-110">Information</span></span>|  
|<span data-ttu-id="d5d68-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="d5d68-111">Channel</span></span>|<span data-ttu-id="d5d68-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="d5d68-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d5d68-113">Description</span><span class="sxs-lookup"><span data-stu-id="d5d68-113">Description</span></span>  

 <span data-ttu-id="d5d68-114">Bu olay, bir `FaultProvider` çağrıldıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="d5d68-114">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d5d68-115">İleti</span><span class="sxs-lookup"><span data-stu-id="d5d68-115">Message</span></span>  

 <span data-ttu-id="d5d68-116">Dağıtıcı, ' %2 ' türünde bir özel durum ile ' %1 ' türünde bir FaultProvider çağırdı.</span><span class="sxs-lookup"><span data-stu-id="d5d68-116">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d5d68-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d5d68-117">Details</span></span>  
  
|<span data-ttu-id="d5d68-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d5d68-118">Data Item Name</span></span>|<span data-ttu-id="d5d68-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d5d68-119">Data Item Type</span></span>|<span data-ttu-id="d5d68-120">Description</span><span class="sxs-lookup"><span data-stu-id="d5d68-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d5d68-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="d5d68-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="d5d68-122">Çağrılan türünün CLR FullName değeri `FaultProvider` .</span><span class="sxs-lookup"><span data-stu-id="d5d68-122">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="d5d68-123">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="d5d68-123">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="d5d68-124">Üzerinde işletitilen özel durumun CLR FullName değeri `FaultProvider` .</span><span class="sxs-lookup"><span data-stu-id="d5d68-124">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="d5d68-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="d5d68-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="d5d68-126">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d5d68-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d5d68-127">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d5d68-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d5d68-128">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="d5d68-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d5d68-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d5d68-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d5d68-130">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d5d68-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
