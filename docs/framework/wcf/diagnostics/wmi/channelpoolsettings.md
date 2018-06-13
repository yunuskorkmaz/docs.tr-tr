---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 48b41d2f3f45cd9c590f87151253450962b994de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485303"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="c49cc-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c49cc-102">ChannelPoolSettings</span></span>
<span data-ttu-id="c49cc-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c49cc-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c49cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c49cc-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c49cc-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c49cc-105">Methods</span></span>  
 <span data-ttu-id="c49cc-106">ChannelPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="c49cc-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c49cc-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c49cc-107">Properties</span></span>  
 <span data-ttu-id="c49cc-108">ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c49cc-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="c49cc-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="c49cc-109">IdleTimeout</span></span>  
 <span data-ttu-id="c49cc-110">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="c49cc-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="c49cc-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="c49cc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c49cc-112">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="c49cc-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="c49cc-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="c49cc-113">LeaseTimeout</span></span>  
 <span data-ttu-id="c49cc-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="c49cc-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="c49cc-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="c49cc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c49cc-116">Zaman aşımından önce tamamlamak bir kira işlemi için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="c49cc-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="c49cc-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="c49cc-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="c49cc-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="c49cc-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c49cc-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="c49cc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c49cc-120">Her uç noktası için giden kanal sayısı.</span><span class="sxs-lookup"><span data-stu-id="c49cc-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c49cc-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c49cc-121">Requirements</span></span>  
  
|<span data-ttu-id="c49cc-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c49cc-122">MOF</span></span>|<span data-ttu-id="c49cc-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c49cc-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c49cc-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="c49cc-124">Namespace</span></span>|<span data-ttu-id="c49cc-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c49cc-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c49cc-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c49cc-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
