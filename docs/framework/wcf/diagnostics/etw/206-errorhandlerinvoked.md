---
description: 'Hakkında daha fazla bilgi edinin: 206-Errorhandlerçağrıldı'
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: addbcbdea25c7f8e7515b743e98e426476fa0b28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783787"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="153bf-103">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="153bf-103">206 - ErrorHandlerInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="153bf-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="153bf-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="153bf-105">ID</span><span class="sxs-lookup"><span data-stu-id="153bf-105">ID</span></span>|<span data-ttu-id="153bf-106">206</span><span class="sxs-lookup"><span data-stu-id="153bf-106">206</span></span>|  
|<span data-ttu-id="153bf-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="153bf-107">Keywords</span></span>|<span data-ttu-id="153bf-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="153bf-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="153bf-109">Level</span><span class="sxs-lookup"><span data-stu-id="153bf-109">Level</span></span>|<span data-ttu-id="153bf-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="153bf-110">Information</span></span>|  
|<span data-ttu-id="153bf-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="153bf-111">Channel</span></span>|<span data-ttu-id="153bf-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="153bf-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="153bf-113">Description</span><span class="sxs-lookup"><span data-stu-id="153bf-113">Description</span></span>  

 <span data-ttu-id="153bf-114">Bu olay, bir `ErrorHandler` hizmet işleminde oluşan bir özel durumu işlemeye yönelik bir fırsata sahip olduktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="153bf-114">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="153bf-115">İleti</span><span class="sxs-lookup"><span data-stu-id="153bf-115">Message</span></span>  

 <span data-ttu-id="153bf-116">Dağıtıcı, ' %3 ' türünde bir özel durum ile ' %1 ' türünde bir ErrorHandler çağırdı.</span><span class="sxs-lookup"><span data-stu-id="153bf-116">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="153bf-117">Errorişlenmiş = = ' %2 '.</span><span class="sxs-lookup"><span data-stu-id="153bf-117">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="153bf-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="153bf-118">Details</span></span>  
  
|<span data-ttu-id="153bf-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="153bf-119">Data Item Name</span></span>|<span data-ttu-id="153bf-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="153bf-120">Data Item Type</span></span>|<span data-ttu-id="153bf-121">Description</span><span class="sxs-lookup"><span data-stu-id="153bf-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="153bf-122">TypeName</span><span class="sxs-lookup"><span data-stu-id="153bf-122">TypeName</span></span>|`xs:string`|<span data-ttu-id="153bf-123">Çağrılan türünün CLR FullName değeri `ErrorHandler` .</span><span class="sxs-lookup"><span data-stu-id="153bf-123">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="153bf-124">İşlenenler</span><span class="sxs-lookup"><span data-stu-id="153bf-124">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="153bf-125">`true` hata işleyicisi hatayı işleirse, tersi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="153bf-125">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="153bf-126">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="153bf-126">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="153bf-127">İşlenmekte olan özel durumun CLR FullName.</span><span class="sxs-lookup"><span data-stu-id="153bf-127">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="153bf-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="153bf-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="153bf-129">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="153bf-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="153bf-130">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="153bf-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="153bf-131">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="153bf-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="153bf-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="153bf-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="153bf-133">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="153bf-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
