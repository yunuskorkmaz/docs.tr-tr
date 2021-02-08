---
description: 'Hakkında daha fazla bilgi edinin: 212-Parameterınspectorbefoyeniden hesapla'
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: aa02ff22b533855716c212d312396e6de23ace42
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794409"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="6dcc7-103">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="6dcc7-103">212 - ParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="6dcc7-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="6dcc7-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6dcc7-105">ID</span><span class="sxs-lookup"><span data-stu-id="6dcc7-105">ID</span></span>|<span data-ttu-id="6dcc7-106">212</span><span class="sxs-lookup"><span data-stu-id="6dcc7-106">212</span></span>|  
|<span data-ttu-id="6dcc7-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="6dcc7-107">Keywords</span></span>|<span data-ttu-id="6dcc7-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6dcc7-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="6dcc7-109">Level</span><span class="sxs-lookup"><span data-stu-id="6dcc7-109">Level</span></span>|<span data-ttu-id="6dcc7-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="6dcc7-110">Information</span></span>|  
|<span data-ttu-id="6dcc7-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="6dcc7-111">Channel</span></span>|<span data-ttu-id="6dcc7-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="6dcc7-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6dcc7-113">Description</span><span class="sxs-lookup"><span data-stu-id="6dcc7-113">Description</span></span>  

 <span data-ttu-id="6dcc7-114">Bu olay, hizmet modeli bir üzerinde yöntemini çağırdıktan sonra yayınlanır `BeforeCall` `ParameterInspector` .</span><span class="sxs-lookup"><span data-stu-id="6dcc7-114">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6dcc7-115">İleti</span><span class="sxs-lookup"><span data-stu-id="6dcc7-115">Message</span></span>  

 <span data-ttu-id="6dcc7-116">Dağıtıcı, ' %1 ' türünde bir Parameterınspector üzerinde ' Befohatırla ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="6dcc7-116">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6dcc7-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="6dcc7-117">Details</span></span>  
  
|<span data-ttu-id="6dcc7-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="6dcc7-118">Data Item Name</span></span>|<span data-ttu-id="6dcc7-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="6dcc7-119">Data Item Type</span></span>|<span data-ttu-id="6dcc7-120">Description</span><span class="sxs-lookup"><span data-stu-id="6dcc7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6dcc7-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="6dcc7-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="6dcc7-122">Çağrılan Inspector türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="6dcc7-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="6dcc7-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="6dcc7-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="6dcc7-124">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6dcc7-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="6dcc7-125">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6dcc7-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="6dcc7-126">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="6dcc7-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="6dcc7-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6dcc7-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6dcc7-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="6dcc7-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
