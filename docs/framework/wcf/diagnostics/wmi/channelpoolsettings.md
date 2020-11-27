---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 3dcc1f3b27d93d5641a4bb2d8082aa3fa88882dc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274224"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="056f4-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="056f4-102">ChannelPoolSettings</span></span>

<span data-ttu-id="056f4-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="056f4-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="056f4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="056f4-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="056f4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="056f4-105">Methods</span></span>  

 <span data-ttu-id="056f4-106">ChannelPoolSettings sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="056f4-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="056f4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="056f4-107">Properties</span></span>  

 <span data-ttu-id="056f4-108">ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="056f4-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="056f4-109">Timeout</span><span class="sxs-lookup"><span data-stu-id="056f4-109">IdleTimeout</span></span>  

 <span data-ttu-id="056f4-110">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="056f4-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="056f4-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="056f4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="056f4-112">Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="056f4-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="056f4-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="056f4-113">LeaseTimeout</span></span>  

 <span data-ttu-id="056f4-114">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="056f4-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="056f4-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="056f4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="056f4-116">Zaman aşımından önce bir kira işleminin tamamlanacağı en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="056f4-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="056f4-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="056f4-117">MaxOutboundChannelsPerEndpoint</span></span>  

 <span data-ttu-id="056f4-118">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="056f4-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="056f4-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="056f4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="056f4-120">Her bitiş noktası için giden kanal sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="056f4-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="056f4-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="056f4-121">Requirements</span></span>  
  
|<span data-ttu-id="056f4-122">MOF</span><span class="sxs-lookup"><span data-stu-id="056f4-122">MOF</span></span>|<span data-ttu-id="056f4-123">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="056f4-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="056f4-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="056f4-124">Namespace</span></span>|<span data-ttu-id="056f4-125">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="056f4-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="056f4-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="056f4-126">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
