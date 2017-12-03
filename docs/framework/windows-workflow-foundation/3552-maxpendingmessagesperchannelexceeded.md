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
ms.openlocfilehash: 5455472a5b9ebdba7aea7d0384ce9cd4a9a2849d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="3e94b-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="3e94b-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="3e94b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3e94b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3e94b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="3e94b-104">ID</span></span>|<span data-ttu-id="3e94b-105">3552</span><span class="sxs-lookup"><span data-stu-id="3e94b-105">3552</span></span>|  
|<span data-ttu-id="3e94b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="3e94b-106">Keywords</span></span>|<span data-ttu-id="3e94b-107">Kota, WFServices</span><span class="sxs-lookup"><span data-stu-id="3e94b-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="3e94b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="3e94b-108">Level</span></span>|<span data-ttu-id="3e94b-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="3e94b-109">Warning</span></span>|  
|<span data-ttu-id="3e94b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="3e94b-110">Channel</span></span>|<span data-ttu-id="3e94b-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="3e94b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3e94b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e94b-112">Description</span></span>  
 <span data-ttu-id="3e94b-113">'Sınırına ulaşıldı MaxPendingMessagesPerChannel' kısıtlama gösterir.</span><span class="sxs-lookup"><span data-stu-id="3e94b-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3e94b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="3e94b-114">Message</span></span>  
 <span data-ttu-id="3e94b-115">'%1' 'MaxPendingMessagesPerChannel' sınırının kısıtlama ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="3e94b-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="3e94b-116">Bu sınırı artırmak için BufferedReceiveServiceBehavior MaxPendingMessagesPerChannel özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3e94b-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3e94b-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3e94b-117">Details</span></span>  
  
|<span data-ttu-id="3e94b-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="3e94b-118">Data Item Name</span></span>|<span data-ttu-id="3e94b-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="3e94b-119">Data Item Type</span></span>|<span data-ttu-id="3e94b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3e94b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3e94b-121">Sınırı</span><span class="sxs-lookup"><span data-stu-id="3e94b-121">Limit</span></span>|<span data-ttu-id="3e94b-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="3e94b-122">xs:string</span></span>|<span data-ttu-id="3e94b-123">MaxPendingMessagesPerChannel kısıtlama sınırı.</span><span class="sxs-lookup"><span data-stu-id="3e94b-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="3e94b-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3e94b-124">AppDomain</span></span>|<span data-ttu-id="3e94b-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="3e94b-125">xs:string</span></span>|<span data-ttu-id="3e94b-126">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="3e94b-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
