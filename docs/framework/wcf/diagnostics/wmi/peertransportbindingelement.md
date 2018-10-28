---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 58bf07b0429ca2435b5aae3683ef69951a10003e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185189"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="5051d-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="5051d-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="5051d-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="5051d-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5051d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5051d-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5051d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5051d-105">Methods</span></span>  
 <span data-ttu-id="5051d-106">Duyduğunuz arabirimi belirtin sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="5051d-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5051d-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5051d-107">Properties</span></span>  
 <span data-ttu-id="5051d-108">Duyduğunuz arabirimi belirtin sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5051d-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="5051d-109">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="5051d-109">ListenIPAddress</span></span>  
 <span data-ttu-id="5051d-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="5051d-110">Data type: string</span></span>  
  
 <span data-ttu-id="5051d-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5051d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5051d-112">Eş düğüm iletileri için dinlediği IP adresi.</span><span class="sxs-lookup"><span data-stu-id="5051d-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="5051d-113">Bağlantı Noktası</span><span class="sxs-lookup"><span data-stu-id="5051d-113">Port</span></span>  
 <span data-ttu-id="5051d-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="5051d-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="5051d-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5051d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5051d-116">Bu kanal iletileri bağlama işlemleri eş ağ arabirim bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="5051d-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="5051d-117">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="5051d-117">Security</span></span>  
 <span data-ttu-id="5051d-118">Veri türü: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="5051d-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="5051d-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5051d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5051d-120">Eş taşıma güvenlik ayarları.</span><span class="sxs-lookup"><span data-stu-id="5051d-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5051d-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5051d-121">Requirements</span></span>  
  
|<span data-ttu-id="5051d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="5051d-122">MOF</span></span>|<span data-ttu-id="5051d-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5051d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5051d-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="5051d-124">Namespace</span></span>|<span data-ttu-id="5051d-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5051d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5051d-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5051d-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
