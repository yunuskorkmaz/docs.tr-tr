---
description: 'Daha fazla bilgi edinin: ChannelPoolSettings'
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: b08c5483e7a0c918393795b4608b9eef16b18341
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757689"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="d9717-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d9717-103">ChannelPoolSettings</span></span>

<span data-ttu-id="d9717-104">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d9717-104">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9717-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d9717-105">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d9717-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d9717-106">Methods</span></span>  

 <span data-ttu-id="d9717-107">ChannelPoolSettings sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d9717-107">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d9717-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d9717-108">Properties</span></span>  

 <span data-ttu-id="d9717-109">ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d9717-109">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="d9717-110">Timeout</span><span class="sxs-lookup"><span data-stu-id="d9717-110">IdleTimeout</span></span>  

 <span data-ttu-id="d9717-111">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="d9717-111">Data type: datetime</span></span>  
  
 <span data-ttu-id="d9717-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d9717-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9717-113">Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="d9717-113">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="d9717-114">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="d9717-114">LeaseTimeout</span></span>  

 <span data-ttu-id="d9717-115">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="d9717-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="d9717-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d9717-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9717-117">Zaman aşımından önce bir kira işleminin tamamlanacağı en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="d9717-117">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="d9717-118">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="d9717-118">MaxOutboundChannelsPerEndpoint</span></span>  

 <span data-ttu-id="d9717-119">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="d9717-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="d9717-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="d9717-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9717-121">Her bitiş noktası için giden kanal sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="d9717-121">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9717-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9717-122">Requirements</span></span>  
  
|<span data-ttu-id="d9717-123">MOF</span><span class="sxs-lookup"><span data-stu-id="d9717-123">MOF</span></span>|<span data-ttu-id="d9717-124">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d9717-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d9717-125">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d9717-125">Namespace</span></span>|<span data-ttu-id="d9717-126">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="d9717-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9717-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9717-127">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
