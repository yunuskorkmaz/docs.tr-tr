---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b9aa7e0d9eaba0181b17b44da1bf871c10af814
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="f0d29-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f0d29-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="f0d29-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f0d29-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0d29-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0d29-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f0d29-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f0d29-105">Methods</span></span>  
 <span data-ttu-id="f0d29-106">TcpTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="f0d29-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f0d29-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f0d29-107">Properties</span></span>  
 <span data-ttu-id="f0d29-108">TcpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f0d29-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="f0d29-109">Tcptransport</span><span class="sxs-lookup"><span data-stu-id="f0d29-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="f0d29-110">Veri türü: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f0d29-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="f0d29-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0d29-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0d29-112">Bağlantı havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="f0d29-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="f0d29-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="f0d29-113">ListenBacklog</span></span>  
 <span data-ttu-id="f0d29-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="f0d29-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f0d29-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0d29-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0d29-116">Bekleyen sıraya alınan bağlantı isteklerini maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="f0d29-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="f0d29-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="f0d29-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="f0d29-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="f0d29-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f0d29-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0d29-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0d29-120">TCP bağlantı noktası paylaşma Bu bağlantı için etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f0d29-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="f0d29-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="f0d29-121">TeredoEnabled</span></span>  
 <span data-ttu-id="f0d29-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="f0d29-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="f0d29-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f0d29-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f0d29-124">Teredo (güvenlik duvarının arkasındaki adresleme istemciler için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="f0d29-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0d29-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0d29-125">Requirements</span></span>  
  
|<span data-ttu-id="f0d29-126">MOF</span><span class="sxs-lookup"><span data-stu-id="f0d29-126">MOF</span></span>|<span data-ttu-id="f0d29-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f0d29-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f0d29-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f0d29-128">Namespace</span></span>|<span data-ttu-id="f0d29-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f0d29-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f0d29-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0d29-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
