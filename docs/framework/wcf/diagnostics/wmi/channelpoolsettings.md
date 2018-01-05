---
title: ChannelPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3995b517b27a5565f7fcb9c11da27c9e1bb40887
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="28d8b-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="28d8b-102">ChannelPoolSettings</span></span>
<span data-ttu-id="28d8b-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="28d8b-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28d8b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28d8b-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="28d8b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="28d8b-105">Methods</span></span>  
 <span data-ttu-id="28d8b-106">ChannelPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="28d8b-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="28d8b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="28d8b-107">Properties</span></span>  
 <span data-ttu-id="28d8b-108">ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="28d8b-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="28d8b-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="28d8b-109">IdleTimeout</span></span>  
 <span data-ttu-id="28d8b-110">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="28d8b-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="28d8b-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="28d8b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28d8b-112">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="28d8b-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="28d8b-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="28d8b-113">LeaseTimeout</span></span>  
 <span data-ttu-id="28d8b-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="28d8b-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="28d8b-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="28d8b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28d8b-116">Zaman aşımından önce tamamlamak bir kira işlemi için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="28d8b-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="28d8b-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="28d8b-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="28d8b-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="28d8b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="28d8b-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="28d8b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="28d8b-120">Her uç noktası için giden kanal sayısı.</span><span class="sxs-lookup"><span data-stu-id="28d8b-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28d8b-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28d8b-121">Requirements</span></span>  
  
|<span data-ttu-id="28d8b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="28d8b-122">MOF</span></span>|<span data-ttu-id="28d8b-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="28d8b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="28d8b-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="28d8b-124">Namespace</span></span>|<span data-ttu-id="28d8b-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="28d8b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28d8b-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="28d8b-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
