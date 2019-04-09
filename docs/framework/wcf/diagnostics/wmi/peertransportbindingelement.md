---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ba9031dad96f12c7c48b03f1da4af1b3adc6dd4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194078"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="e08ca-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e08ca-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="e08ca-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e08ca-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e08ca-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e08ca-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e08ca-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e08ca-105">Methods</span></span>  
 <span data-ttu-id="e08ca-106">Duyduğunuz arabirimi belirtin sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e08ca-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e08ca-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e08ca-107">Properties</span></span>  
 <span data-ttu-id="e08ca-108">Duyduğunuz arabirimi belirtin sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e08ca-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="e08ca-109">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="e08ca-109">ListenIPAddress</span></span>  
 <span data-ttu-id="e08ca-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e08ca-110">Data type: string</span></span>  
  
 <span data-ttu-id="e08ca-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e08ca-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e08ca-112">Eş düğüm iletileri için dinlediği IP adresi.</span><span class="sxs-lookup"><span data-stu-id="e08ca-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="e08ca-113">Bağlantı Noktası</span><span class="sxs-lookup"><span data-stu-id="e08ca-113">Port</span></span>  
 <span data-ttu-id="e08ca-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="e08ca-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e08ca-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e08ca-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e08ca-116">Bu kanal iletileri bağlama işlemleri eş ağ arabirim bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="e08ca-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="e08ca-117">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="e08ca-117">Security</span></span>  
 <span data-ttu-id="e08ca-118">Veri türü: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="e08ca-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="e08ca-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e08ca-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e08ca-120">Eş taşıma güvenlik ayarları.</span><span class="sxs-lookup"><span data-stu-id="e08ca-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e08ca-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e08ca-121">Requirements</span></span>  
  
|<span data-ttu-id="e08ca-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e08ca-122">MOF</span></span>|<span data-ttu-id="e08ca-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e08ca-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e08ca-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e08ca-124">Namespace</span></span>|<span data-ttu-id="e08ca-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e08ca-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e08ca-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e08ca-126">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
