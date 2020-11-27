---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ae6a3448896cb206bce8867daf7104c3e484ecc8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269021"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="0bdb1-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0bdb1-102">PeerTransportBindingElement</span></span>

<span data-ttu-id="0bdb1-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="0bdb1-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bdb1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="0bdb1-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="0bdb1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0bdb1-105">Methods</span></span>  

 <span data-ttu-id="0bdb1-106">PeerTransportBindingElement Class herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="0bdb1-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0bdb1-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="0bdb1-107">Properties</span></span>  

 <span data-ttu-id="0bdb1-108">PeerTransportBindingElement class aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0bdb1-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="0bdb1-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="0bdb1-109">ListenIPAddress</span></span>  

 <span data-ttu-id="0bdb1-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="0bdb1-110">Data type: string</span></span>  
  
 <span data-ttu-id="0bdb1-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="0bdb1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0bdb1-112">Eş düğümün iletileri dinlediği IP adresi.</span><span class="sxs-lookup"><span data-stu-id="0bdb1-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="0bdb1-113">Bağlantı noktası</span><span class="sxs-lookup"><span data-stu-id="0bdb1-113">Port</span></span>  

 <span data-ttu-id="0bdb1-114">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="0bdb1-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="0bdb1-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="0bdb1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0bdb1-116">Bu bağlamanın eş kanal iletilerini işlediği ağ arabirimi bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="0bdb1-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="0bdb1-117">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="0bdb1-117">Security</span></span>  

 <span data-ttu-id="0bdb1-118">Veri türü: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="0bdb1-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="0bdb1-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="0bdb1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0bdb1-120">Eş taşıma güvenlik ayarları.</span><span class="sxs-lookup"><span data-stu-id="0bdb1-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bdb1-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0bdb1-121">Requirements</span></span>  
  
|<span data-ttu-id="0bdb1-122">MOF</span><span class="sxs-lookup"><span data-stu-id="0bdb1-122">MOF</span></span>|<span data-ttu-id="0bdb1-123">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0bdb1-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0bdb1-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="0bdb1-124">Namespace</span></span>|<span data-ttu-id="0bdb1-125">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="0bdb1-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0bdb1-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bdb1-126">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
