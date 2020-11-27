---
title: 207 - FaultProviderInvoked
ms.date: 03/30/2017
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
ms.openlocfilehash: 71381c9eee6aed4792500c8558db88e239bf89f7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295177"
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="a2fa0-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="a2fa0-102">207 - FaultProviderInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="a2fa0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a2fa0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a2fa0-104">ID</span><span class="sxs-lookup"><span data-stu-id="a2fa0-104">ID</span></span>|<span data-ttu-id="a2fa0-105">207</span><span class="sxs-lookup"><span data-stu-id="a2fa0-105">207</span></span>|  
|<span data-ttu-id="a2fa0-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="a2fa0-106">Keywords</span></span>|<span data-ttu-id="a2fa0-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a2fa0-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a2fa0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a2fa0-108">Level</span></span>|<span data-ttu-id="a2fa0-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="a2fa0-109">Information</span></span>|  
|<span data-ttu-id="a2fa0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a2fa0-110">Channel</span></span>|<span data-ttu-id="a2fa0-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="a2fa0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a2fa0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2fa0-112">Description</span></span>  

 <span data-ttu-id="a2fa0-113">Bu olay, bir `FaultProvider` çağrıldıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a2fa0-114">İleti</span><span class="sxs-lookup"><span data-stu-id="a2fa0-114">Message</span></span>  

 <span data-ttu-id="a2fa0-115">Dağıtıcı, ' %2 ' türünde bir özel durum ile ' %1 ' türünde bir FaultProvider çağırdı.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a2fa0-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a2fa0-116">Details</span></span>  
  
|<span data-ttu-id="a2fa0-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a2fa0-117">Data Item Name</span></span>|<span data-ttu-id="a2fa0-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a2fa0-118">Data Item Type</span></span>|<span data-ttu-id="a2fa0-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2fa0-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a2fa0-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="a2fa0-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="a2fa0-121">Çağrılan türünün CLR FullName değeri `FaultProvider` .</span><span class="sxs-lookup"><span data-stu-id="a2fa0-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="a2fa0-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="a2fa0-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="a2fa0-123">Üzerinde işletitilen özel durumun CLR FullName değeri `FaultProvider` .</span><span class="sxs-lookup"><span data-stu-id="a2fa0-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="a2fa0-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="a2fa0-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="a2fa0-125">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a2fa0-126">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a2fa0-127">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a2fa0-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a2fa0-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a2fa0-129">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="a2fa0-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
