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
ms.openlocfilehash: e97e934673efbc6d0f72751c7cb1de6fba84a141
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="aead3-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="aead3-102">ChannelPoolSettings</span></span>
<span data-ttu-id="aead3-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="aead3-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aead3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aead3-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="aead3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aead3-105">Methods</span></span>  
 <span data-ttu-id="aead3-106">ChannelPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="aead3-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="aead3-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="aead3-107">Properties</span></span>  
 <span data-ttu-id="aead3-108">ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="aead3-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="aead3-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="aead3-109">IdleTimeout</span></span>  
 <span data-ttu-id="aead3-110">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="aead3-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="aead3-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aead3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aead3-112">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="aead3-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="aead3-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="aead3-113">LeaseTimeout</span></span>  
 <span data-ttu-id="aead3-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="aead3-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="aead3-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aead3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aead3-116">Zaman aşımından önce tamamlamak bir kira işlemi için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="aead3-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="aead3-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="aead3-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="aead3-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="aead3-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="aead3-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="aead3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="aead3-120">Her uç noktası için giden kanal sayısı.</span><span class="sxs-lookup"><span data-stu-id="aead3-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aead3-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aead3-121">Requirements</span></span>  
  
|<span data-ttu-id="aead3-122">MOF</span><span class="sxs-lookup"><span data-stu-id="aead3-122">MOF</span></span>|<span data-ttu-id="aead3-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="aead3-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="aead3-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="aead3-124">Namespace</span></span>|<span data-ttu-id="aead3-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aead3-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aead3-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aead3-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
