---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 806066a8845068413d2a52c78878f76b5f5fa34f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250378"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="f79af-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="f79af-102">OneWayBindingElement</span></span>

<span data-ttu-id="f79af-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="f79af-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f79af-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f79af-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f79af-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f79af-105">Methods</span></span>  

 <span data-ttu-id="f79af-106">OneWayBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="f79af-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f79af-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f79af-107">Properties</span></span>  

 <span data-ttu-id="f79af-108">OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f79af-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="f79af-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f79af-109">ChannelPoolSettings</span></span>  

 <span data-ttu-id="f79af-110">Veri türü: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f79af-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="f79af-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f79af-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79af-112">Kanal havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="f79af-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="f79af-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="f79af-113">MaxAcceptedChannels</span></span>  

 <span data-ttu-id="f79af-114">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="f79af-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f79af-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f79af-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79af-116">Kabul edilen en fazla kanal sayısı.</span><span class="sxs-lookup"><span data-stu-id="f79af-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="f79af-117">Packetyönlendirilebilir</span><span class="sxs-lookup"><span data-stu-id="f79af-117">PacketRoutable</span></span>  

 <span data-ttu-id="f79af-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="f79af-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f79af-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="f79af-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f79af-120">Paketin yönlendirilebilir olup olmadığını gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="f79af-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f79af-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f79af-121">Requirements</span></span>  
  
|<span data-ttu-id="f79af-122">MOF</span><span class="sxs-lookup"><span data-stu-id="f79af-122">MOF</span></span>|<span data-ttu-id="f79af-123">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f79af-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f79af-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f79af-124">Namespace</span></span>|<span data-ttu-id="f79af-125">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="f79af-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f79af-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f79af-126">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
