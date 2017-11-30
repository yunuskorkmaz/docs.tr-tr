---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cdb89eb9f2a50db20f6da53a2b3f527aef8c0ed1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="ce564-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="ce564-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="ce564-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ce564-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ce564-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ce564-104">ID</span></span>|<span data-ttu-id="ce564-105">208</span><span class="sxs-lookup"><span data-stu-id="ce564-105">208</span></span>|  
|<span data-ttu-id="ce564-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ce564-106">Keywords</span></span>|<span data-ttu-id="ce564-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ce564-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ce564-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ce564-108">Level</span></span>|<span data-ttu-id="ce564-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="ce564-109">Information</span></span>|  
|<span data-ttu-id="ce564-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ce564-110">Channel</span></span>|<span data-ttu-id="ce564-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ce564-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ce564-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce564-112">Description</span></span>  
 <span data-ttu-id="ce564-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `AfterReceive` ileti denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ce564-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ce564-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ce564-114">Message</span></span>  
 <span data-ttu-id="ce564-115">Dağıtıcı '%1' türünde bir MessageInspector ' AfterReceiveReply' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ce564-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ce564-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ce564-116">Details</span></span>  
  
|<span data-ttu-id="ce564-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ce564-117">Data Item Name</span></span>|<span data-ttu-id="ce564-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ce564-118">Data Item Type</span></span>|<span data-ttu-id="ce564-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ce564-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ce564-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="ce564-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="ce564-121">Çağrılan türünün CLR FullName `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="ce564-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="ce564-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="ce564-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="ce564-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ce564-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ce564-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="ce564-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ce564-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="ce564-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ce564-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ce564-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ce564-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ce564-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
