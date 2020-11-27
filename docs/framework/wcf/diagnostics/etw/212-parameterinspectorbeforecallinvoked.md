---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 28c2aca4555d2e4ff498e450deae55ad6a87743c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279044"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="ca573-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="ca573-102">212 - ParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="ca573-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ca573-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ca573-104">ID</span><span class="sxs-lookup"><span data-stu-id="ca573-104">ID</span></span>|<span data-ttu-id="ca573-105">212</span><span class="sxs-lookup"><span data-stu-id="ca573-105">212</span></span>|  
|<span data-ttu-id="ca573-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ca573-106">Keywords</span></span>|<span data-ttu-id="ca573-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ca573-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ca573-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ca573-108">Level</span></span>|<span data-ttu-id="ca573-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="ca573-109">Information</span></span>|  
|<span data-ttu-id="ca573-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ca573-110">Channel</span></span>|<span data-ttu-id="ca573-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ca573-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ca573-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca573-112">Description</span></span>  

 <span data-ttu-id="ca573-113">Bu olay, hizmet modeli bir üzerinde yöntemini çağırdıktan sonra yayınlanır `BeforeCall` `ParameterInspector` .</span><span class="sxs-lookup"><span data-stu-id="ca573-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ca573-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ca573-114">Message</span></span>  

 <span data-ttu-id="ca573-115">Dağıtıcı, ' %1 ' türünde bir Parameterınspector üzerinde ' Befohatırla ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="ca573-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ca573-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ca573-116">Details</span></span>  
  
|<span data-ttu-id="ca573-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ca573-117">Data Item Name</span></span>|<span data-ttu-id="ca573-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ca573-118">Data Item Type</span></span>|<span data-ttu-id="ca573-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ca573-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ca573-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="ca573-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="ca573-121">Çağrılan Inspector türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="ca573-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="ca573-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="ca573-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="ca573-123">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ca573-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ca573-124">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ca573-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ca573-125">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="ca573-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ca573-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ca573-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ca573-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ca573-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
