---
description: 'Daha fazla bilgi edinin: PeerTransportBindingElement'
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: b1ca8020f51a5f9b121f7d238d82b9971d13cdd4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757338"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="9fb68-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9fb68-103">PeerTransportBindingElement</span></span>

<span data-ttu-id="9fb68-104">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9fb68-104">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb68-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9fb68-105">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9fb68-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9fb68-106">Methods</span></span>  

 <span data-ttu-id="9fb68-107">PeerTransportBindingElement Class herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9fb68-107">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9fb68-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9fb68-108">Properties</span></span>  

 <span data-ttu-id="9fb68-109">PeerTransportBindingElement class aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9fb68-109">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="9fb68-110">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="9fb68-110">ListenIPAddress</span></span>  

 <span data-ttu-id="9fb68-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9fb68-111">Data type: string</span></span>  
  
 <span data-ttu-id="9fb68-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9fb68-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fb68-113">Eş düğümün iletileri dinlediği IP adresi.</span><span class="sxs-lookup"><span data-stu-id="9fb68-113">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="9fb68-114">Bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="9fb68-114">Port</span></span>  

 <span data-ttu-id="9fb68-115">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="9fb68-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="9fb68-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9fb68-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fb68-117">Bu bağlamanın eş kanal iletilerini işlediği ağ arabirimi bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="9fb68-117">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="9fb68-118">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="9fb68-118">Security</span></span>  

 <span data-ttu-id="9fb68-119">Veri türü: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9fb68-119">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="9fb68-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="9fb68-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9fb68-121">Eş taşıma güvenlik ayarları.</span><span class="sxs-lookup"><span data-stu-id="9fb68-121">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fb68-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9fb68-122">Requirements</span></span>  
  
|<span data-ttu-id="9fb68-123">MOF</span><span class="sxs-lookup"><span data-stu-id="9fb68-123">MOF</span></span>|<span data-ttu-id="9fb68-124">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9fb68-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9fb68-125">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9fb68-125">Namespace</span></span>|<span data-ttu-id="9fb68-126">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="9fb68-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9fb68-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fb68-127">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
