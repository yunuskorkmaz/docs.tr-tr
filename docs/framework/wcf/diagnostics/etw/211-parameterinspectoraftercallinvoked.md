---
title: 211 - ParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 78424b8057518f5d9f201ead33b2784ffeeb7e58
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="88cd3-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="88cd3-102">211 - ParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="88cd3-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="88cd3-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="88cd3-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="88cd3-104">ID</span></span>|<span data-ttu-id="88cd3-105">211</span><span class="sxs-lookup"><span data-stu-id="88cd3-105">211</span></span>|  
|<span data-ttu-id="88cd3-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="88cd3-106">Keywords</span></span>|<span data-ttu-id="88cd3-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="88cd3-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="88cd3-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="88cd3-108">Level</span></span>|<span data-ttu-id="88cd3-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="88cd3-109">Information</span></span>|  
|<span data-ttu-id="88cd3-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="88cd3-110">Channel</span></span>|<span data-ttu-id="88cd3-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="88cd3-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="88cd3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88cd3-112">Description</span></span>  
 <span data-ttu-id="88cd3-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `AfterCall` yöntemi bir `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="88cd3-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="88cd3-114">İleti</span><span class="sxs-lookup"><span data-stu-id="88cd3-114">Message</span></span>  
 <span data-ttu-id="88cd3-115">Dağıtıcı '%1' türünde bir ParameterInspector ' AfterCall' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="88cd3-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="88cd3-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="88cd3-116">Details</span></span>  
  
|<span data-ttu-id="88cd3-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="88cd3-117">Data Item Name</span></span>|<span data-ttu-id="88cd3-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="88cd3-118">Data Item Type</span></span>|<span data-ttu-id="88cd3-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88cd3-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="88cd3-120">Tür adı</span><span class="sxs-lookup"><span data-stu-id="88cd3-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="88cd3-121">Çağrılan türünün CLR FullName `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="88cd3-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="88cd3-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="88cd3-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="88cd3-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="88cd3-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="88cd3-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="88cd3-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="88cd3-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="88cd3-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="88cd3-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="88cd3-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="88cd3-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="88cd3-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
