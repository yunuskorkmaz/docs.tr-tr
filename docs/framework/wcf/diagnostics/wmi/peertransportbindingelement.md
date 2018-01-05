---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25893b1f3cf6cf20ae674bade5090a70c5f381a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="9a744-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9a744-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="9a744-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9a744-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a744-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a744-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9a744-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9a744-105">Methods</span></span>  
 <span data-ttu-id="9a744-106">Duyduğunuz arabirimi belirtin sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="9a744-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9a744-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9a744-107">Properties</span></span>  
 <span data-ttu-id="9a744-108">Duyduğunuz arabirimi belirtin sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9a744-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="9a744-109">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="9a744-109">ListenIPAddress</span></span>  
 <span data-ttu-id="9a744-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9a744-110">Data type: string</span></span>  
  
 <span data-ttu-id="9a744-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9a744-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a744-112">Eş düğüm için iletileri dinlediği IP adresi.</span><span class="sxs-lookup"><span data-stu-id="9a744-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="9a744-113">Bağlantı Noktası</span><span class="sxs-lookup"><span data-stu-id="9a744-113">Port</span></span>  
 <span data-ttu-id="9a744-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9a744-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="9a744-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9a744-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a744-116">Ağ arabirimi, bu kanal iletileri bağlama işlemleri eş bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="9a744-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="9a744-117">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="9a744-117">Security</span></span>  
 <span data-ttu-id="9a744-118">Veri türü: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9a744-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="9a744-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9a744-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a744-120">Eş taşıma güvenlik ayarları.</span><span class="sxs-lookup"><span data-stu-id="9a744-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a744-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a744-121">Requirements</span></span>  
  
|<span data-ttu-id="9a744-122">MOF</span><span class="sxs-lookup"><span data-stu-id="9a744-122">MOF</span></span>|<span data-ttu-id="9a744-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9a744-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9a744-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9a744-124">Namespace</span></span>|<span data-ttu-id="9a744-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9a744-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a744-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a744-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
