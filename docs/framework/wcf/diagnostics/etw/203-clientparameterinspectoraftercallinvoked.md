---
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1173aaa4bf01b324c8cd6088cd5646bc67f08c72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="149d8-102">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="149d8-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="149d8-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="149d8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="149d8-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="149d8-104">ID</span></span>|<span data-ttu-id="149d8-105">203</span><span class="sxs-lookup"><span data-stu-id="149d8-105">203</span></span>|  
|<span data-ttu-id="149d8-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="149d8-106">Keywords</span></span>|<span data-ttu-id="149d8-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="149d8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="149d8-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="149d8-108">Level</span></span>|<span data-ttu-id="149d8-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="149d8-109">Information</span></span>|  
|<span data-ttu-id="149d8-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="149d8-110">Channel</span></span>|<span data-ttu-id="149d8-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="149d8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="149d8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="149d8-112">Description</span></span>  
 <span data-ttu-id="149d8-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `AfterCall` istemci parametre denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="149d8-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="149d8-114">İleti</span><span class="sxs-lookup"><span data-stu-id="149d8-114">Message</span></span>  
 <span data-ttu-id="149d8-115">Dağıtıcı '%1' türünde bir ClientParameterInspector ' AfterCall' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="149d8-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="149d8-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="149d8-116">Details</span></span>  
  
|<span data-ttu-id="149d8-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="149d8-117">Data Item Name</span></span>|<span data-ttu-id="149d8-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="149d8-118">Data Item Type</span></span>|<span data-ttu-id="149d8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="149d8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="149d8-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="149d8-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="149d8-121">Çağrılan Denetçisi'nin türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="149d8-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="149d8-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="149d8-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="149d8-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="149d8-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="149d8-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="149d8-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="149d8-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="149d8-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="149d8-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="149d8-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="149d8-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="149d8-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
