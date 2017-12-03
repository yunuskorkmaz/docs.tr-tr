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
ms.openlocfilehash: 193000acf2f3c8a0eddb2552559ee40a0f5fced9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="9a692-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9a692-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="9a692-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9a692-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a692-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a692-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9a692-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9a692-105">Methods</span></span>  
 <span data-ttu-id="9a692-106">Duyduğunuz arabirimi belirtin sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="9a692-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9a692-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9a692-107">Properties</span></span>  
 <span data-ttu-id="9a692-108">Duyduğunuz arabirimi belirtin sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9a692-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="9a692-109">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="9a692-109">ListenIPAddress</span></span>  
 <span data-ttu-id="9a692-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="9a692-110">Data type: string</span></span>  
  
 <span data-ttu-id="9a692-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9a692-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a692-112">Eş düğüm için iletileri dinlediği IP adresi.</span><span class="sxs-lookup"><span data-stu-id="9a692-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="9a692-113">Bağlantı Noktası</span><span class="sxs-lookup"><span data-stu-id="9a692-113">Port</span></span>  
 <span data-ttu-id="9a692-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9a692-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="9a692-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9a692-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a692-116">Ağ arabirimi, bu kanal iletileri bağlama işlemleri eş bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="9a692-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="9a692-117">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="9a692-117">Security</span></span>  
 <span data-ttu-id="9a692-118">Veri türü: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9a692-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="9a692-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9a692-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a692-120">Eş taşıma güvenlik ayarları.</span><span class="sxs-lookup"><span data-stu-id="9a692-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a692-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a692-121">Requirements</span></span>  
  
|<span data-ttu-id="9a692-122">MOF</span><span class="sxs-lookup"><span data-stu-id="9a692-122">MOF</span></span>|<span data-ttu-id="9a692-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9a692-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9a692-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9a692-124">Namespace</span></span>|<span data-ttu-id="9a692-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9a692-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a692-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a692-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
