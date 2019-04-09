---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 8900af77d0d385bb68b4b85e1d15be57bb7a8d14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131917"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="c0e0f-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c0e0f-102">ChannelPoolSettings</span></span>
<span data-ttu-id="c0e0f-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c0e0f-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0e0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0e0f-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c0e0f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c0e0f-105">Methods</span></span>  
 <span data-ttu-id="c0e0f-106">ChannelPoolSettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="c0e0f-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c0e0f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c0e0f-107">Properties</span></span>  
 <span data-ttu-id="c0e0f-108">ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c0e0f-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="c0e0f-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="c0e0f-109">IdleTimeout</span></span>  
 <span data-ttu-id="c0e0f-110">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="c0e0f-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="c0e0f-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="c0e0f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0e0f-112">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="c0e0f-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="c0e0f-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="c0e0f-113">LeaseTimeout</span></span>  
 <span data-ttu-id="c0e0f-114">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="c0e0f-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="c0e0f-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="c0e0f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0e0f-116">Bir kira işlemi zaman aşımına uğramadan önce tamamlanması için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="c0e0f-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="c0e0f-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="c0e0f-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="c0e0f-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="c0e0f-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c0e0f-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="c0e0f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c0e0f-120">Giden kanallar için her uç nokta sayısı.</span><span class="sxs-lookup"><span data-stu-id="c0e0f-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0e0f-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0e0f-121">Requirements</span></span>  
  
|<span data-ttu-id="c0e0f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="c0e0f-122">MOF</span></span>|<span data-ttu-id="c0e0f-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c0e0f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c0e0f-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="c0e0f-124">Namespace</span></span>|<span data-ttu-id="c0e0f-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c0e0f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0e0f-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0e0f-126">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
