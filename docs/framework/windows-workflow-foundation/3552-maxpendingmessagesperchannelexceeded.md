---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511237"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="cce6a-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="cce6a-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="cce6a-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cce6a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cce6a-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="cce6a-104">ID</span></span>|<span data-ttu-id="cce6a-105">3552</span><span class="sxs-lookup"><span data-stu-id="cce6a-105">3552</span></span>|  
|<span data-ttu-id="cce6a-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="cce6a-106">Keywords</span></span>|<span data-ttu-id="cce6a-107">Kota, WFServices</span><span class="sxs-lookup"><span data-stu-id="cce6a-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="cce6a-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="cce6a-108">Level</span></span>|<span data-ttu-id="cce6a-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="cce6a-109">Warning</span></span>|  
|<span data-ttu-id="cce6a-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="cce6a-110">Channel</span></span>|<span data-ttu-id="cce6a-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="cce6a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cce6a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cce6a-112">Description</span></span>  
 <span data-ttu-id="cce6a-113">'Sınırına ulaşıldı MaxPendingMessagesPerChannel' kısıtlama gösterir.</span><span class="sxs-lookup"><span data-stu-id="cce6a-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cce6a-114">İleti</span><span class="sxs-lookup"><span data-stu-id="cce6a-114">Message</span></span>  
 <span data-ttu-id="cce6a-115">'%1' 'MaxPendingMessagesPerChannel' sınırının kısıtlama ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="cce6a-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="cce6a-116">Bu sınırı artırmak için BufferedReceiveServiceBehavior MaxPendingMessagesPerChannel özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cce6a-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cce6a-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="cce6a-117">Details</span></span>  
  
|<span data-ttu-id="cce6a-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="cce6a-118">Data Item Name</span></span>|<span data-ttu-id="cce6a-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="cce6a-119">Data Item Type</span></span>|<span data-ttu-id="cce6a-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cce6a-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cce6a-121">Sınırı</span><span class="sxs-lookup"><span data-stu-id="cce6a-121">Limit</span></span>|<span data-ttu-id="cce6a-122">xs: String</span><span class="sxs-lookup"><span data-stu-id="cce6a-122">xs:string</span></span>|<span data-ttu-id="cce6a-123">MaxPendingMessagesPerChannel kısıtlama sınırı.</span><span class="sxs-lookup"><span data-stu-id="cce6a-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="cce6a-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cce6a-124">AppDomain</span></span>|<span data-ttu-id="cce6a-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="cce6a-125">xs:string</span></span>|<span data-ttu-id="cce6a-126">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="cce6a-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
