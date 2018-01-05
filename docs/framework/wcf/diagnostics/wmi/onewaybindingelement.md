---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47de8c2449c46b12b8d10ac2a5269a18d1454f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="d88a4-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="d88a4-102">OneWayBindingElement</span></span>
<span data-ttu-id="d88a4-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="d88a4-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d88a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d88a4-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d88a4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d88a4-105">Methods</span></span>  
 <span data-ttu-id="d88a4-106">OneWayBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d88a4-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d88a4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d88a4-107">Properties</span></span>  
 <span data-ttu-id="d88a4-108">OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d88a4-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="d88a4-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d88a4-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="d88a4-110">Veri türü: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d88a4-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="d88a4-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d88a4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d88a4-112">Kanal havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="d88a4-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="d88a4-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="d88a4-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="d88a4-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="d88a4-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="d88a4-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d88a4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d88a4-116">Kabul edilen kanal sayısı.</span><span class="sxs-lookup"><span data-stu-id="d88a4-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="d88a4-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="d88a4-117">PacketRoutable</span></span>  
 <span data-ttu-id="d88a4-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d88a4-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d88a4-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d88a4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d88a4-120">Paket yönlendirilebilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d88a4-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d88a4-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d88a4-121">Requirements</span></span>  
  
|<span data-ttu-id="d88a4-122">MOF</span><span class="sxs-lookup"><span data-stu-id="d88a4-122">MOF</span></span>|<span data-ttu-id="d88a4-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d88a4-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d88a4-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d88a4-124">Namespace</span></span>|<span data-ttu-id="d88a4-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d88a4-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d88a4-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d88a4-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
