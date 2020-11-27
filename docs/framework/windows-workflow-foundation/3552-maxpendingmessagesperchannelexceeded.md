---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: bd3e7539922e6c430c4ffe5bd96ef1ac7dbd098f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261169"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="b7061-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="b7061-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>

## <a name="properties"></a><span data-ttu-id="b7061-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b7061-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b7061-104">ID</span><span class="sxs-lookup"><span data-stu-id="b7061-104">ID</span></span>|<span data-ttu-id="b7061-105">3552</span><span class="sxs-lookup"><span data-stu-id="b7061-105">3552</span></span>|  
|<span data-ttu-id="b7061-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="b7061-106">Keywords</span></span>|<span data-ttu-id="b7061-107">Kota, Wfservice</span><span class="sxs-lookup"><span data-stu-id="b7061-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="b7061-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="b7061-108">Level</span></span>|<span data-ttu-id="b7061-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="b7061-109">Warning</span></span>|  
|<span data-ttu-id="b7061-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="b7061-110">Channel</span></span>|<span data-ttu-id="b7061-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="b7061-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b7061-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7061-112">Description</span></span>  

 <span data-ttu-id="b7061-113">' Maxpendingiletiperchannel ' limitinin isabet aldığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7061-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b7061-114">İleti</span><span class="sxs-lookup"><span data-stu-id="b7061-114">Message</span></span>  

 <span data-ttu-id="b7061-115">' Maxpendingiletiperchannel ' kısıtlama ' %1 ' sınırına ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="b7061-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="b7061-116">Bu sınırı artırmak için, BufferedReceiveServiceBehavior üzerindeki Maxpendingiletiperchannel özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b7061-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="b7061-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b7061-117">Details</span></span>  
  
|<span data-ttu-id="b7061-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="b7061-118">Data Item Name</span></span>|<span data-ttu-id="b7061-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="b7061-119">Data Item Type</span></span>|<span data-ttu-id="b7061-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7061-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b7061-121">Sınır</span><span class="sxs-lookup"><span data-stu-id="b7061-121">Limit</span></span>|<span data-ttu-id="b7061-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7061-122">xs:string</span></span>|<span data-ttu-id="b7061-123">Maxpendingiletiperchannel kısıtlama sınırı.</span><span class="sxs-lookup"><span data-stu-id="b7061-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="b7061-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="b7061-124">AppDomain</span></span>|<span data-ttu-id="b7061-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="b7061-125">xs:string</span></span>|<span data-ttu-id="b7061-126">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="b7061-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
