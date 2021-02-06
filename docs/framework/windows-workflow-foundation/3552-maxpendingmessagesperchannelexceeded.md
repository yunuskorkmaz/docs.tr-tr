---
description: 'Hakkında daha fazla bilgi edinin: 3552-Maxpendingiletiperchannelexcebaşında'
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: 5fb2d27f7d68716cebf2cfaafd21851226a456e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99631443"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="d63f1-103">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="d63f1-103">3552 - MaxPendingMessagesPerChannelExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="d63f1-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d63f1-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d63f1-105">ID</span><span class="sxs-lookup"><span data-stu-id="d63f1-105">ID</span></span>|<span data-ttu-id="d63f1-106">3552</span><span class="sxs-lookup"><span data-stu-id="d63f1-106">3552</span></span>|  
|<span data-ttu-id="d63f1-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="d63f1-107">Keywords</span></span>|<span data-ttu-id="d63f1-108">Kota, Wfservice</span><span class="sxs-lookup"><span data-stu-id="d63f1-108">Quota, WFServices</span></span>|  
|<span data-ttu-id="d63f1-109">Level</span><span class="sxs-lookup"><span data-stu-id="d63f1-109">Level</span></span>|<span data-ttu-id="d63f1-110">Uyarı</span><span class="sxs-lookup"><span data-stu-id="d63f1-110">Warning</span></span>|  
|<span data-ttu-id="d63f1-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="d63f1-111">Channel</span></span>|<span data-ttu-id="d63f1-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="d63f1-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d63f1-113">Description</span><span class="sxs-lookup"><span data-stu-id="d63f1-113">Description</span></span>  

 <span data-ttu-id="d63f1-114">' Maxpendingiletiperchannel ' limitinin isabet aldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d63f1-114">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d63f1-115">İleti</span><span class="sxs-lookup"><span data-stu-id="d63f1-115">Message</span></span>  

 <span data-ttu-id="d63f1-116">' Maxpendingiletiperchannel ' kısıtlama ' %1 ' sınırına ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="d63f1-116">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="d63f1-117">Bu sınırı artırmak için, BufferedReceiveServiceBehavior üzerindeki Maxpendingiletiperchannel özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d63f1-117">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d63f1-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d63f1-118">Details</span></span>  
  
|<span data-ttu-id="d63f1-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d63f1-119">Data Item Name</span></span>|<span data-ttu-id="d63f1-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d63f1-120">Data Item Type</span></span>|<span data-ttu-id="d63f1-121">Description</span><span class="sxs-lookup"><span data-stu-id="d63f1-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d63f1-122">Sınır</span><span class="sxs-lookup"><span data-stu-id="d63f1-122">Limit</span></span>|<span data-ttu-id="d63f1-123">xs: String</span><span class="sxs-lookup"><span data-stu-id="d63f1-123">xs:string</span></span>|<span data-ttu-id="d63f1-124">Maxpendingiletiperchannel kısıtlama sınırı.</span><span class="sxs-lookup"><span data-stu-id="d63f1-124">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="d63f1-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d63f1-125">AppDomain</span></span>|<span data-ttu-id="d63f1-126">xs: String</span><span class="sxs-lookup"><span data-stu-id="d63f1-126">xs:string</span></span>|<span data-ttu-id="d63f1-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d63f1-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
