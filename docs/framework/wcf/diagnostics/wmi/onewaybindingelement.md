---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 34220a3651819978f5f597fdc67d54630ec5e059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195820"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="2e042-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="2e042-102">OneWayBindingElement</span></span>
<span data-ttu-id="2e042-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="2e042-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e042-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2e042-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2e042-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2e042-105">Methods</span></span>  
 <span data-ttu-id="2e042-106">OneWayBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="2e042-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2e042-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2e042-107">Properties</span></span>  
 <span data-ttu-id="2e042-108">OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2e042-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="2e042-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2e042-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="2e042-110">Veri türü: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2e042-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="2e042-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2e042-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e042-112">Kanal havuzu ayarlarını.</span><span class="sxs-lookup"><span data-stu-id="2e042-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="2e042-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="2e042-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="2e042-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2e042-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="2e042-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2e042-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e042-116">Kabul edilen kanallar maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="2e042-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="2e042-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="2e042-117">PacketRoutable</span></span>  
 <span data-ttu-id="2e042-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="2e042-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e042-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2e042-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e042-120">Paket yönlendirilebilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="2e042-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e042-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e042-121">Requirements</span></span>  
  
|<span data-ttu-id="2e042-122">MOF</span><span class="sxs-lookup"><span data-stu-id="2e042-122">MOF</span></span>|<span data-ttu-id="2e042-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2e042-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2e042-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2e042-124">Namespace</span></span>|<span data-ttu-id="2e042-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2e042-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e042-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2e042-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
