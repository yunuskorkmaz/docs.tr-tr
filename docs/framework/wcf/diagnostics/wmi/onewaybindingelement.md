---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: ee7cfed20234175ba54dd25dbbbab4615c1ed7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485770"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="23883-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="23883-102">OneWayBindingElement</span></span>
<span data-ttu-id="23883-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="23883-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23883-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23883-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="23883-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="23883-105">Methods</span></span>  
 <span data-ttu-id="23883-106">OneWayBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="23883-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="23883-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="23883-107">Properties</span></span>  
 <span data-ttu-id="23883-108">OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="23883-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="23883-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="23883-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="23883-110">Veri türü: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="23883-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="23883-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="23883-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23883-112">Kanal havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="23883-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="23883-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="23883-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="23883-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="23883-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="23883-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="23883-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23883-116">Kabul edilen kanal sayısı.</span><span class="sxs-lookup"><span data-stu-id="23883-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="23883-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="23883-117">PacketRoutable</span></span>  
 <span data-ttu-id="23883-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="23883-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="23883-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="23883-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="23883-120">Paket yönlendirilebilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="23883-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23883-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23883-121">Requirements</span></span>  
  
|<span data-ttu-id="23883-122">MOF</span><span class="sxs-lookup"><span data-stu-id="23883-122">MOF</span></span>|<span data-ttu-id="23883-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="23883-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="23883-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="23883-124">Namespace</span></span>|<span data-ttu-id="23883-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="23883-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23883-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="23883-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
