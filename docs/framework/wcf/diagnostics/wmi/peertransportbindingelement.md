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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48364c2bcfa50476ac5f9f00f87c17f97dc14017
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="b3dfd-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b3dfd-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="b3dfd-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b3dfd-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3dfd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3dfd-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b3dfd-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b3dfd-105">Methods</span></span>  
 <span data-ttu-id="b3dfd-106">Duyduğunuz arabirimi belirtin sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="b3dfd-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b3dfd-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b3dfd-107">Properties</span></span>  
 <span data-ttu-id="b3dfd-108">Duyduğunuz arabirimi belirtin sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b3dfd-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="b3dfd-109">ListenIpAddress</span><span class="sxs-lookup"><span data-stu-id="b3dfd-109">ListenIPAddress</span></span>  
 <span data-ttu-id="b3dfd-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b3dfd-110">Data type: string</span></span>  
  
 <span data-ttu-id="b3dfd-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b3dfd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3dfd-112">Eş düğüm için iletileri dinlediği IP adresi.</span><span class="sxs-lookup"><span data-stu-id="b3dfd-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="b3dfd-113">Bağlantı Noktası</span><span class="sxs-lookup"><span data-stu-id="b3dfd-113">Port</span></span>  
 <span data-ttu-id="b3dfd-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="b3dfd-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b3dfd-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b3dfd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3dfd-116">Ağ arabirimi, bu kanal iletileri bağlama işlemleri eş bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="b3dfd-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="b3dfd-117">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="b3dfd-117">Security</span></span>  
 <span data-ttu-id="b3dfd-118">Veri türü: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="b3dfd-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="b3dfd-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b3dfd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3dfd-120">Eş taşıma güvenlik ayarları.</span><span class="sxs-lookup"><span data-stu-id="b3dfd-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3dfd-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3dfd-121">Requirements</span></span>  
  
|<span data-ttu-id="b3dfd-122">MOF</span><span class="sxs-lookup"><span data-stu-id="b3dfd-122">MOF</span></span>|<span data-ttu-id="b3dfd-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b3dfd-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b3dfd-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b3dfd-124">Namespace</span></span>|<span data-ttu-id="b3dfd-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b3dfd-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3dfd-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3dfd-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
