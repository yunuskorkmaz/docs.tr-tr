---
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 99415733624752217d32f6f026a419b2b32bfa7b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244619"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="a8390-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="a8390-102">206 - ErrorHandlerInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="a8390-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a8390-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a8390-104">ID</span><span class="sxs-lookup"><span data-stu-id="a8390-104">ID</span></span>|<span data-ttu-id="a8390-105">206</span><span class="sxs-lookup"><span data-stu-id="a8390-105">206</span></span>|  
|<span data-ttu-id="a8390-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a8390-106">Keywords</span></span>|<span data-ttu-id="a8390-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a8390-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a8390-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a8390-108">Level</span></span>|<span data-ttu-id="a8390-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="a8390-109">Information</span></span>|  
|<span data-ttu-id="a8390-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a8390-110">Channel</span></span>|<span data-ttu-id="a8390-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="a8390-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a8390-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8390-112">Description</span></span>  

 <span data-ttu-id="a8390-113">Bu olay, bir `ErrorHandler` hizmet işleminde oluşan bir özel durumu işlemeye yönelik bir fırsata sahip olduktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="a8390-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a8390-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a8390-114">Message</span></span>  

 <span data-ttu-id="a8390-115">Dağıtıcı, ' %3 ' türünde bir özel durum ile ' %1 ' türünde bir ErrorHandler çağırdı.</span><span class="sxs-lookup"><span data-stu-id="a8390-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="a8390-116">Errorişlenmiş = = ' %2 '.</span><span class="sxs-lookup"><span data-stu-id="a8390-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a8390-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a8390-117">Details</span></span>  
  
|<span data-ttu-id="a8390-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a8390-118">Data Item Name</span></span>|<span data-ttu-id="a8390-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a8390-119">Data Item Type</span></span>|<span data-ttu-id="a8390-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a8390-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a8390-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="a8390-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="a8390-122">Çağrılan türünün CLR FullName değeri `ErrorHandler` .</span><span class="sxs-lookup"><span data-stu-id="a8390-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="a8390-123">İşlenenler</span><span class="sxs-lookup"><span data-stu-id="a8390-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="a8390-124">`true` hata işleyicisi hatayı işleirse, tersi durumda `false` .</span><span class="sxs-lookup"><span data-stu-id="a8390-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="a8390-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="a8390-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="a8390-126">İşlenmekte olan özel durumun CLR FullName.</span><span class="sxs-lookup"><span data-stu-id="a8390-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="a8390-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="a8390-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="a8390-128">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a8390-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a8390-129">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a8390-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a8390-130">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="a8390-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a8390-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a8390-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a8390-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a8390-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
