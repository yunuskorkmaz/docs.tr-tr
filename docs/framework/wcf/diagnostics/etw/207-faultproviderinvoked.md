---
title: 207 - FaultProviderInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b730d903-01c2-4deb-85a4-da12f8a21fe4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 71fce60ca658c159df11588be149cda17ad2303d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="207---faultproviderinvoked"></a><span data-ttu-id="bd1e8-102">207 - FaultProviderInvoked</span><span class="sxs-lookup"><span data-stu-id="bd1e8-102">207 - FaultProviderInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="bd1e8-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bd1e8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bd1e8-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="bd1e8-104">ID</span></span>|<span data-ttu-id="bd1e8-105">207</span><span class="sxs-lookup"><span data-stu-id="bd1e8-105">207</span></span>|  
|<span data-ttu-id="bd1e8-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="bd1e8-106">Keywords</span></span>|<span data-ttu-id="bd1e8-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bd1e8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="bd1e8-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="bd1e8-108">Level</span></span>|<span data-ttu-id="bd1e8-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="bd1e8-109">Information</span></span>|  
|<span data-ttu-id="bd1e8-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="bd1e8-110">Channel</span></span>|<span data-ttu-id="bd1e8-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="bd1e8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bd1e8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd1e8-112">Description</span></span>  
 <span data-ttu-id="bd1e8-113">Bu olay sonra yayılan bir `FaultProvider` çağrılmış.</span><span class="sxs-lookup"><span data-stu-id="bd1e8-113">This event is emitted after a `FaultProvider` has been invoked.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bd1e8-114">İleti</span><span class="sxs-lookup"><span data-stu-id="bd1e8-114">Message</span></span>  
 <span data-ttu-id="bd1e8-115">Dağıtıcı '%2' türünde bir özel durum ile '%1' türünde bir FaultProvider çağrılır.</span><span class="sxs-lookup"><span data-stu-id="bd1e8-115">The Dispatcher invoked a FaultProvider of type '%1' with an exception of type '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bd1e8-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="bd1e8-116">Details</span></span>  
  
|<span data-ttu-id="bd1e8-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="bd1e8-117">Data Item Name</span></span>|<span data-ttu-id="bd1e8-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="bd1e8-118">Data Item Type</span></span>|<span data-ttu-id="bd1e8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bd1e8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bd1e8-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="bd1e8-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="bd1e8-121">Çağrılan türünün CLR FullName `FaultProvider`.</span><span class="sxs-lookup"><span data-stu-id="bd1e8-121">The CLR FullName of the type of the invoked `FaultProvider`.</span></span>|  
|<span data-ttu-id="bd1e8-122">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="bd1e8-122">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="bd1e8-123">Özel durumun CLR FullName, `FaultProvider` üzerinde çalıştırılan.</span><span class="sxs-lookup"><span data-stu-id="bd1e8-123">The CLR FullName of the exception that the `FaultProvider` has operated on.</span></span>|  
|<span data-ttu-id="bd1e8-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="bd1e8-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="bd1e8-125">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bd1e8-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="bd1e8-126">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="bd1e8-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="bd1e8-127">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="bd1e8-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="bd1e8-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="bd1e8-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="bd1e8-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="bd1e8-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
