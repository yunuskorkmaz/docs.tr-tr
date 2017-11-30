---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: baf466bf63dcb9335a20eed8b563c222e09c7055
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="e1c98-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="e1c98-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="e1c98-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e1c98-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e1c98-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="e1c98-104">ID</span></span>|<span data-ttu-id="e1c98-105">202</span><span class="sxs-lookup"><span data-stu-id="e1c98-105">202</span></span>|  
|<span data-ttu-id="e1c98-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="e1c98-106">Keywords</span></span>|<span data-ttu-id="e1c98-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e1c98-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e1c98-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e1c98-108">Level</span></span>|<span data-ttu-id="e1c98-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="e1c98-109">Information</span></span>|  
|<span data-ttu-id="e1c98-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e1c98-110">Channel</span></span>|<span data-ttu-id="e1c98-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="e1c98-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e1c98-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1c98-112">Description</span></span>  
 <span data-ttu-id="e1c98-113">Bu olay, hizmet modeli çağrılmış sonra yayınlanır `BeforeSendRequest` istemci ileti denetçisi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e1c98-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e1c98-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e1c98-114">Message</span></span>  
 <span data-ttu-id="e1c98-115">Dağıtıcı '%1' türünde bir ClientMessageInspector ' BeforeSendRequest' çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e1c98-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e1c98-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e1c98-116">Details</span></span>  
  
|<span data-ttu-id="e1c98-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e1c98-117">Data Item Name</span></span>|<span data-ttu-id="e1c98-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e1c98-118">Data Item Type</span></span>|<span data-ttu-id="e1c98-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1c98-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e1c98-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="e1c98-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="e1c98-121">Çağrılan Denetçisi'nin türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="e1c98-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="e1c98-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="e1c98-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="e1c98-123">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e1c98-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e1c98-124">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="e1c98-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e1c98-125">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="e1c98-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e1c98-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e1c98-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e1c98-127">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e1c98-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
