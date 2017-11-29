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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a56616e97526b2d410d18d97dc1391c6fc32cc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="843e5-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="843e5-102">ChannelPoolSettings</span></span>
<span data-ttu-id="843e5-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="843e5-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="843e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="843e5-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="843e5-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="843e5-105">Methods</span></span>  
 <span data-ttu-id="843e5-106">ChannelPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="843e5-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="843e5-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="843e5-107">Properties</span></span>  
 <span data-ttu-id="843e5-108">ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="843e5-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="843e5-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="843e5-109">IdleTimeout</span></span>  
 <span data-ttu-id="843e5-110">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="843e5-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="843e5-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="843e5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="843e5-112">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="843e5-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="843e5-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="843e5-113">LeaseTimeout</span></span>  
 <span data-ttu-id="843e5-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="843e5-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="843e5-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="843e5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="843e5-116">Zaman aşımından önce tamamlamak bir kira işlemi için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="843e5-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="843e5-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="843e5-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="843e5-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="843e5-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="843e5-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="843e5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="843e5-120">Her uç noktası için giden kanal sayısı.</span><span class="sxs-lookup"><span data-stu-id="843e5-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="843e5-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="843e5-121">Requirements</span></span>  
  
|<span data-ttu-id="843e5-122">MOF</span><span class="sxs-lookup"><span data-stu-id="843e5-122">MOF</span></span>|<span data-ttu-id="843e5-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="843e5-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="843e5-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="843e5-124">Namespace</span></span>|<span data-ttu-id="843e5-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="843e5-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="843e5-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="843e5-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
