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
ms.openlocfilehash: 1a0bbe31095a59be4b091de6974ae0173753e240
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="499---transferemitted"></a><span data-ttu-id="79b44-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="79b44-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="79b44-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="79b44-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="79b44-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="79b44-104">ID</span></span>|<span data-ttu-id="79b44-105">499</span><span class="sxs-lookup"><span data-stu-id="79b44-105">499</span></span>|  
|<span data-ttu-id="79b44-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="79b44-106">Keywords</span></span>|<span data-ttu-id="79b44-107">Sorun giderme, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="79b44-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="79b44-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="79b44-108">Level</span></span>|<span data-ttu-id="79b44-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="79b44-109">LogAlways</span></span>|  
|<span data-ttu-id="79b44-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="79b44-110">Channel</span></span>|<span data-ttu-id="79b44-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="79b44-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="79b44-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79b44-112">Description</span></span>  
 <span data-ttu-id="79b44-113">Bu olay, aktarım olay gerçekleştiğinde yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="79b44-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="79b44-114">İleti</span><span class="sxs-lookup"><span data-stu-id="79b44-114">Message</span></span>  
 <span data-ttu-id="79b44-115">Gösterilen olay aktarın.</span><span class="sxs-lookup"><span data-stu-id="79b44-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="79b44-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="79b44-116">Details</span></span>  
  
|<span data-ttu-id="79b44-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="79b44-117">Data Item Name</span></span>|<span data-ttu-id="79b44-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="79b44-118">Data Item Type</span></span>|<span data-ttu-id="79b44-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79b44-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="79b44-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="79b44-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="79b44-121">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="79b44-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="79b44-122">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="79b44-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="79b44-123">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="79b44-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="79b44-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="79b44-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="79b44-125">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="79b44-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
