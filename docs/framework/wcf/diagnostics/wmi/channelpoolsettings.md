---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 4a3e45140765f99f4a30b77fc9d02b167601b50b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591490"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="0410c-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0410c-102">ChannelPoolSettings</span></span>
<span data-ttu-id="0410c-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="0410c-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0410c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0410c-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0410c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0410c-105">Methods</span></span>  
 <span data-ttu-id="0410c-106">ChannelPoolSettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="0410c-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0410c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0410c-107">Properties</span></span>  
 <span data-ttu-id="0410c-108">ChannelPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0410c-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="0410c-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="0410c-109">IdleTimeout</span></span>  
 <span data-ttu-id="0410c-110">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="0410c-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="0410c-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0410c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0410c-112">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="0410c-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="0410c-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="0410c-113">LeaseTimeout</span></span>  
 <span data-ttu-id="0410c-114">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="0410c-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="0410c-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0410c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0410c-116">Bir kira işlemi zaman aşımına uğramadan önce tamamlanması için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="0410c-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="0410c-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="0410c-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="0410c-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="0410c-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="0410c-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="0410c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0410c-120">Giden kanallar için her uç nokta sayısı.</span><span class="sxs-lookup"><span data-stu-id="0410c-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0410c-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0410c-121">Requirements</span></span>  
  
|<span data-ttu-id="0410c-122">MOF</span><span class="sxs-lookup"><span data-stu-id="0410c-122">MOF</span></span>|<span data-ttu-id="0410c-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0410c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0410c-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="0410c-124">Namespace</span></span>|<span data-ttu-id="0410c-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0410c-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0410c-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0410c-126">See also</span></span>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
