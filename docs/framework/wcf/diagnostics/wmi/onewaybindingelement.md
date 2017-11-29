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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a43707f25a9ee1beb1ce7adac36a2c4a55cab6d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="d5109-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="d5109-102">OneWayBindingElement</span></span>
<span data-ttu-id="d5109-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="d5109-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5109-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5109-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d5109-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d5109-105">Methods</span></span>  
 <span data-ttu-id="d5109-106">OneWayBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="d5109-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d5109-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d5109-107">Properties</span></span>  
 <span data-ttu-id="d5109-108">OneWayBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d5109-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="d5109-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d5109-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="d5109-110">Veri türü: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d5109-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="d5109-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d5109-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5109-112">Kanal havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="d5109-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="d5109-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="d5109-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="d5109-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="d5109-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="d5109-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d5109-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5109-116">Kabul edilen kanal sayısı.</span><span class="sxs-lookup"><span data-stu-id="d5109-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="d5109-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="d5109-117">PacketRoutable</span></span>  
 <span data-ttu-id="d5109-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="d5109-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d5109-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d5109-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5109-120">Paket yönlendirilebilir olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="d5109-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5109-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5109-121">Requirements</span></span>  
  
|<span data-ttu-id="d5109-122">MOF</span><span class="sxs-lookup"><span data-stu-id="d5109-122">MOF</span></span>|<span data-ttu-id="d5109-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d5109-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d5109-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d5109-124">Namespace</span></span>|<span data-ttu-id="d5109-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d5109-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5109-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5109-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
