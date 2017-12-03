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
ms.openlocfilehash: abaacfb6541d41019a8d0cd6df53913c6b7911f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="cc010-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="cc010-102">OneWayBindingElement</span></span>
<span data-ttu-id="cc010-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="cc010-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc010-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cc010-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cc010-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cc010-105">Methods</span></span>  
 <span data-ttu-id="cc010-106">OneWayBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="cc010-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cc010-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cc010-107">Properties</span></span>  
 <span data-ttu-id="cc010-108">OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cc010-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="cc010-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="cc010-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="cc010-110">Veri türü: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="cc010-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="cc010-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cc010-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc010-112">Kanal havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="cc010-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="cc010-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="cc010-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="cc010-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cc010-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="cc010-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cc010-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc010-116">Kabul edilen kanal sayısı.</span><span class="sxs-lookup"><span data-stu-id="cc010-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="cc010-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="cc010-117">PacketRoutable</span></span>  
 <span data-ttu-id="cc010-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cc010-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="cc010-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cc010-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cc010-120">Paket yönlendirilebilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="cc010-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc010-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cc010-121">Requirements</span></span>  
  
|<span data-ttu-id="cc010-122">MOF</span><span class="sxs-lookup"><span data-stu-id="cc010-122">MOF</span></span>|<span data-ttu-id="cc010-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cc010-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cc010-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cc010-124">Namespace</span></span>|<span data-ttu-id="cc010-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cc010-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc010-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cc010-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
