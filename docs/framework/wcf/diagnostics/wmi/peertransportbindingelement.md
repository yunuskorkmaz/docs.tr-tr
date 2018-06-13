---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 68e6a25e4e3f47c556363e2fd5aa8d3bb9946449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485651"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="4ee2e-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4ee2e-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="4ee2e-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4ee2e-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ee2e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4ee2e-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4ee2e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4ee2e-105">Methods</span></span>  
 <span data-ttu-id="4ee2e-106">Duyduğunuz arabirimi belirtin sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="4ee2e-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4ee2e-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4ee2e-107">Properties</span></span>  
 <span data-ttu-id="4ee2e-108">Duyduğunuz arabirimi belirtin sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4ee2e-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="4ee2e-109">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="4ee2e-109">ListenIPAddress</span></span>  
 <span data-ttu-id="4ee2e-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="4ee2e-110">Data type: string</span></span>  
  
 <span data-ttu-id="4ee2e-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="4ee2e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4ee2e-112">Eş düğüm için iletileri dinlediği IP adresi.</span><span class="sxs-lookup"><span data-stu-id="4ee2e-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="4ee2e-113">Bağlantı Noktası</span><span class="sxs-lookup"><span data-stu-id="4ee2e-113">Port</span></span>  
 <span data-ttu-id="4ee2e-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="4ee2e-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4ee2e-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="4ee2e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4ee2e-116">Ağ arabirimi, bu kanal iletileri bağlama işlemleri eş bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="4ee2e-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="4ee2e-117">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="4ee2e-117">Security</span></span>  
 <span data-ttu-id="4ee2e-118">Veri türü: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4ee2e-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="4ee2e-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="4ee2e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4ee2e-120">Eş taşıma güvenlik ayarları.</span><span class="sxs-lookup"><span data-stu-id="4ee2e-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ee2e-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ee2e-121">Requirements</span></span>  
  
|<span data-ttu-id="4ee2e-122">MOF</span><span class="sxs-lookup"><span data-stu-id="4ee2e-122">MOF</span></span>|<span data-ttu-id="4ee2e-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4ee2e-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4ee2e-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="4ee2e-124">Namespace</span></span>|<span data-ttu-id="4ee2e-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4ee2e-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4ee2e-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ee2e-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
