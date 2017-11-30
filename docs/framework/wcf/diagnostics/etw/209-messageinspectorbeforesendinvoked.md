---
title: 209 - MessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8de4338fd9d1d18ab1f689df39b2247a29d2dcf5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="302a8-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="302a8-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="302a8-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="302a8-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="302a8-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="302a8-104">ID</span></span>|<span data-ttu-id="302a8-105">209</span><span class="sxs-lookup"><span data-stu-id="302a8-105">209</span></span>|  
|<span data-ttu-id="302a8-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="302a8-106">Keywords</span></span>|<span data-ttu-id="302a8-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="302a8-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="302a8-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="302a8-108">Level</span></span>|<span data-ttu-id="302a8-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="302a8-109">Information</span></span>|  
|<span data-ttu-id="302a8-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="302a8-110">Channel</span></span>|<span data-ttu-id="302a8-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="302a8-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="302a8-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="302a8-112">Description</span></span>  
 <span data-ttu-id="302a8-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `BeforeSend` ileti denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="302a8-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="302a8-114">İleti</span><span class="sxs-lookup"><span data-stu-id="302a8-114">Message</span></span>  
 <span data-ttu-id="302a8-115">Dağıtıcı '%1' türünde bir MessageInspector ' BeforeSendRequest' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="302a8-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="302a8-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="302a8-116">Details</span></span>  
  
|<span data-ttu-id="302a8-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="302a8-117">Data Item Name</span></span>|<span data-ttu-id="302a8-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="302a8-118">Data Item Type</span></span>|<span data-ttu-id="302a8-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="302a8-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="302a8-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="302a8-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="302a8-121">Çağrılan türünün CLR FullName `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="302a8-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="302a8-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="302a8-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="302a8-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="302a8-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="302a8-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="302a8-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="302a8-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="302a8-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="302a8-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="302a8-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="302a8-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="302a8-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
