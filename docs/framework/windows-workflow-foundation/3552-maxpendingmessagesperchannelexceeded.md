---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf90e78ed7fbfe500ac52e6629d31bd0aff97bd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="43fc0-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="43fc0-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="43fc0-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="43fc0-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43fc0-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="43fc0-104">ID</span></span>|<span data-ttu-id="43fc0-105">3552</span><span class="sxs-lookup"><span data-stu-id="43fc0-105">3552</span></span>|  
|<span data-ttu-id="43fc0-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="43fc0-106">Keywords</span></span>|<span data-ttu-id="43fc0-107">Kota, WFServices</span><span class="sxs-lookup"><span data-stu-id="43fc0-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="43fc0-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="43fc0-108">Level</span></span>|<span data-ttu-id="43fc0-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="43fc0-109">Warning</span></span>|  
|<span data-ttu-id="43fc0-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="43fc0-110">Channel</span></span>|<span data-ttu-id="43fc0-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="43fc0-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="43fc0-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43fc0-112">Description</span></span>  
 <span data-ttu-id="43fc0-113">'Sınırına ulaşıldı MaxPendingMessagesPerChannel' kısıtlama gösterir.</span><span class="sxs-lookup"><span data-stu-id="43fc0-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="43fc0-114">İleti</span><span class="sxs-lookup"><span data-stu-id="43fc0-114">Message</span></span>  
 <span data-ttu-id="43fc0-115">'%1' 'MaxPendingMessagesPerChannel' sınırının kısıtlama ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="43fc0-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="43fc0-116">Bu sınırı artırmak için BufferedReceiveServiceBehavior MaxPendingMessagesPerChannel özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="43fc0-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="43fc0-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="43fc0-117">Details</span></span>  
  
|<span data-ttu-id="43fc0-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="43fc0-118">Data Item Name</span></span>|<span data-ttu-id="43fc0-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="43fc0-119">Data Item Type</span></span>|<span data-ttu-id="43fc0-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43fc0-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="43fc0-121">Sınırı</span><span class="sxs-lookup"><span data-stu-id="43fc0-121">Limit</span></span>|<span data-ttu-id="43fc0-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="43fc0-122">xs:string</span></span>|<span data-ttu-id="43fc0-123">MaxPendingMessagesPerChannel kısıtlama sınırı.</span><span class="sxs-lookup"><span data-stu-id="43fc0-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="43fc0-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="43fc0-124">AppDomain</span></span>|<span data-ttu-id="43fc0-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="43fc0-125">xs:string</span></span>|<span data-ttu-id="43fc0-126">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="43fc0-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
