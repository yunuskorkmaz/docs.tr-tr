---
description: 'Daha fazla bilgi edinin: OneWayBindingElement'
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 9c2ccc301bd854c7b85fcc53551ed6def329a8fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803093"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="c9794-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="c9794-103">OneWayBindingElement</span></span>

<span data-ttu-id="c9794-104">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="c9794-104">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9794-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9794-105">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c9794-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c9794-106">Methods</span></span>  

 <span data-ttu-id="c9794-107">OneWayBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="c9794-107">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c9794-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c9794-108">Properties</span></span>  

 <span data-ttu-id="c9794-109">OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c9794-109">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="c9794-110">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c9794-110">ChannelPoolSettings</span></span>  

 <span data-ttu-id="c9794-111">Veri türü: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="c9794-111">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="c9794-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c9794-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9794-113">Kanal havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="c9794-113">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="c9794-114">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="c9794-114">MaxAcceptedChannels</span></span>  

 <span data-ttu-id="c9794-115">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="c9794-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="c9794-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c9794-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9794-117">Kabul edilen en fazla kanal sayısı.</span><span class="sxs-lookup"><span data-stu-id="c9794-117">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="c9794-118">Packetyönlendirilebilir</span><span class="sxs-lookup"><span data-stu-id="c9794-118">PacketRoutable</span></span>  

 <span data-ttu-id="c9794-119">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="c9794-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="c9794-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="c9794-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c9794-121">Paketin yönlendirilebilir olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="c9794-121">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9794-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9794-122">Requirements</span></span>  
  
|<span data-ttu-id="c9794-123">MOF</span><span class="sxs-lookup"><span data-stu-id="c9794-123">MOF</span></span>|<span data-ttu-id="c9794-124">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="c9794-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c9794-125">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="c9794-125">Namespace</span></span>|<span data-ttu-id="c9794-126">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="c9794-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c9794-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9794-127">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
