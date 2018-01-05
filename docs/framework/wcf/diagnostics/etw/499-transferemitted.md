---
title: 499 - TransferEmitted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1034ae6bd6072a3849d72fafcad55c61e500439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="335d4-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="335d4-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="335d4-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="335d4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="335d4-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="335d4-104">ID</span></span>|<span data-ttu-id="335d4-105">499</span><span class="sxs-lookup"><span data-stu-id="335d4-105">499</span></span>|  
|<span data-ttu-id="335d4-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="335d4-106">Keywords</span></span>|<span data-ttu-id="335d4-107">Sorun giderme, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="335d4-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="335d4-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="335d4-108">Level</span></span>|<span data-ttu-id="335d4-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="335d4-109">LogAlways</span></span>|  
|<span data-ttu-id="335d4-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="335d4-110">Channel</span></span>|<span data-ttu-id="335d4-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="335d4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="335d4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="335d4-112">Description</span></span>  
 <span data-ttu-id="335d4-113">Bu olay, aktarım olay gerçekleştiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="335d4-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="335d4-114">İleti</span><span class="sxs-lookup"><span data-stu-id="335d4-114">Message</span></span>  
 <span data-ttu-id="335d4-115">Gösterilen olay aktarın.</span><span class="sxs-lookup"><span data-stu-id="335d4-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="335d4-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="335d4-116">Details</span></span>  
  
|<span data-ttu-id="335d4-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="335d4-117">Data Item Name</span></span>|<span data-ttu-id="335d4-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="335d4-118">Data Item Type</span></span>|<span data-ttu-id="335d4-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="335d4-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="335d4-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="335d4-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="335d4-121">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="335d4-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="335d4-122">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="335d4-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="335d4-123">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="335d4-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="335d4-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="335d4-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="335d4-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="335d4-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
