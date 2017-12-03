---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b30e53803692b7127d63a67b2c2c4178dc645db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="84e70-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="84e70-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="84e70-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="84e70-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84e70-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="84e70-104">ID</span></span>|<span data-ttu-id="84e70-105">204</span><span class="sxs-lookup"><span data-stu-id="84e70-105">204</span></span>|  
|<span data-ttu-id="84e70-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="84e70-106">Keywords</span></span>|<span data-ttu-id="84e70-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="84e70-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="84e70-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="84e70-108">Level</span></span>|<span data-ttu-id="84e70-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="84e70-109">Information</span></span>|  
|<span data-ttu-id="84e70-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="84e70-110">Channel</span></span>|<span data-ttu-id="84e70-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="84e70-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="84e70-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84e70-112">Description</span></span>  
 <span data-ttu-id="84e70-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `BeforeCall` istemci parametre denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="84e70-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="84e70-114">İleti</span><span class="sxs-lookup"><span data-stu-id="84e70-114">Message</span></span>  
 <span data-ttu-id="84e70-115">Dağıtıcı '%1' türünde bir ClientParameterInspector ' BeforeCall' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="84e70-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="84e70-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="84e70-116">Details</span></span>  
  
|<span data-ttu-id="84e70-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="84e70-117">Data Item Name</span></span>|<span data-ttu-id="84e70-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="84e70-118">Data Item Type</span></span>|<span data-ttu-id="84e70-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="84e70-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="84e70-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="84e70-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="84e70-121">Çağrılan Denetçisi'nin türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="84e70-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="84e70-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="84e70-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="84e70-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84e70-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="84e70-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="84e70-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="84e70-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="84e70-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="84e70-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="84e70-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="84e70-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="84e70-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
