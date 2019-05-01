---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945944"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a><span data-ttu-id="ccbd1-102">3552 - MaxPendingMessagesPerChannelExceeded</span><span class="sxs-lookup"><span data-stu-id="ccbd1-102">3552 - MaxPendingMessagesPerChannelExceeded</span></span>
## <a name="properties"></a><span data-ttu-id="ccbd1-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ccbd1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ccbd1-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ccbd1-104">ID</span></span>|<span data-ttu-id="ccbd1-105">3552</span><span class="sxs-lookup"><span data-stu-id="ccbd1-105">3552</span></span>|  
|<span data-ttu-id="ccbd1-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ccbd1-106">Keywords</span></span>|<span data-ttu-id="ccbd1-107">Kota, WFServices</span><span class="sxs-lookup"><span data-stu-id="ccbd1-107">Quota, WFServices</span></span>|  
|<span data-ttu-id="ccbd1-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ccbd1-108">Level</span></span>|<span data-ttu-id="ccbd1-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="ccbd1-109">Warning</span></span>|  
|<span data-ttu-id="ccbd1-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ccbd1-110">Channel</span></span>|<span data-ttu-id="ccbd1-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ccbd1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ccbd1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccbd1-112">Description</span></span>  
 <span data-ttu-id="ccbd1-113">Kısıtlama 'MaxPendingMessagesPerChannel limite ulaşılmadan önce' gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccbd1-113">Indicates the throttle 'MaxPendingMessagesPerChannel' limit was hit.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ccbd1-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ccbd1-114">Message</span></span>  
 <span data-ttu-id="ccbd1-115">'%1' 'MaxPendingMessagesPerChannel' sınırını azaltma ulaşıldı.</span><span class="sxs-lookup"><span data-stu-id="ccbd1-115">The throttle 'MaxPendingMessagesPerChannel' limit of  '%1' was hit.</span></span> <span data-ttu-id="ccbd1-116">Bu sınırı artırmak için BufferedReceiveServiceBehavior MaxPendingMessagesPerChannel özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ccbd1-116">To increase this limit, adjust the MaxPendingMessagesPerChannel property on BufferedReceiveServiceBehavior.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ccbd1-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ccbd1-117">Details</span></span>  
  
|<span data-ttu-id="ccbd1-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ccbd1-118">Data Item Name</span></span>|<span data-ttu-id="ccbd1-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ccbd1-119">Data Item Type</span></span>|<span data-ttu-id="ccbd1-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccbd1-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ccbd1-121">Sınır</span><span class="sxs-lookup"><span data-stu-id="ccbd1-121">Limit</span></span>|<span data-ttu-id="ccbd1-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccbd1-122">xs:string</span></span>|<span data-ttu-id="ccbd1-123">MaxPendingMessagesPerChannel kısıtlama sınırı.</span><span class="sxs-lookup"><span data-stu-id="ccbd1-123">The limit of the MaxPendingMessagesPerChannel throttle.</span></span>|  
|<span data-ttu-id="ccbd1-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ccbd1-124">AppDomain</span></span>|<span data-ttu-id="ccbd1-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="ccbd1-125">xs:string</span></span>|<span data-ttu-id="ccbd1-126">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ccbd1-126">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
