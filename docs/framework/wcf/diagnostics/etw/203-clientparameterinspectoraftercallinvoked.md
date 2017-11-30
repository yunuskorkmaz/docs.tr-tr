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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b736d9e2827708caea54fbe230b0b638492adb96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="f0551-102">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="f0551-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="f0551-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f0551-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0551-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="f0551-104">ID</span></span>|<span data-ttu-id="f0551-105">203</span><span class="sxs-lookup"><span data-stu-id="f0551-105">203</span></span>|  
|<span data-ttu-id="f0551-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="f0551-106">Keywords</span></span>|<span data-ttu-id="f0551-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f0551-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f0551-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f0551-108">Level</span></span>|<span data-ttu-id="f0551-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="f0551-109">Information</span></span>|  
|<span data-ttu-id="f0551-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f0551-110">Channel</span></span>|<span data-ttu-id="f0551-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="f0551-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f0551-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0551-112">Description</span></span>  
 <span data-ttu-id="f0551-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `AfterCall` istemci parametre denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f0551-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f0551-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f0551-114">Message</span></span>  
 <span data-ttu-id="f0551-115">Dağıtıcı '%1' türünde bir ClientParameterInspector ' AfterCall' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f0551-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f0551-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f0551-116">Details</span></span>  
  
|<span data-ttu-id="f0551-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f0551-117">Data Item Name</span></span>|<span data-ttu-id="f0551-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f0551-118">Data Item Type</span></span>|<span data-ttu-id="f0551-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f0551-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f0551-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="f0551-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="f0551-121">Çağrılan Denetçisi'nin türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="f0551-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="f0551-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="f0551-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="f0551-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f0551-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f0551-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="f0551-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f0551-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="f0551-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f0551-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f0551-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f0551-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f0551-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
