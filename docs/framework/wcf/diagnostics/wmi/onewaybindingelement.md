---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 016ff823eb2c84a9f54c0763edadef1224e31517
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168746"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="e14d3-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="e14d3-102">OneWayBindingElement</span></span>
<span data-ttu-id="e14d3-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="e14d3-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e14d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e14d3-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e14d3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e14d3-105">Methods</span></span>  
 <span data-ttu-id="e14d3-106">OneWayBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e14d3-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e14d3-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e14d3-107">Properties</span></span>  
 <span data-ttu-id="e14d3-108">OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e14d3-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="e14d3-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e14d3-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="e14d3-110">Veri türü: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e14d3-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="e14d3-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e14d3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e14d3-112">Kanal havuzu ayarlarını.</span><span class="sxs-lookup"><span data-stu-id="e14d3-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="e14d3-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="e14d3-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="e14d3-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e14d3-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e14d3-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e14d3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e14d3-116">Kabul edilen kanallar maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="e14d3-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="e14d3-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="e14d3-117">PacketRoutable</span></span>  
 <span data-ttu-id="e14d3-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="e14d3-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="e14d3-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e14d3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e14d3-120">Paket yönlendirilebilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="e14d3-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e14d3-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e14d3-121">Requirements</span></span>  
  
|<span data-ttu-id="e14d3-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e14d3-122">MOF</span></span>|<span data-ttu-id="e14d3-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e14d3-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e14d3-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e14d3-124">Namespace</span></span>|<span data-ttu-id="e14d3-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e14d3-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e14d3-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e14d3-126">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
