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
ms.workload: dotnet
ms.openlocfilehash: 6e230cbccee211fbda219000fbbd2cda5275776b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="cca5d-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="cca5d-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="cca5d-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="cca5d-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cca5d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cca5d-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cca5d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cca5d-105">Methods</span></span>  
 <span data-ttu-id="cca5d-106">TcpTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="cca5d-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cca5d-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cca5d-107">Properties</span></span>  
 <span data-ttu-id="cca5d-108">TcpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cca5d-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="cca5d-109">Tcptransport</span><span class="sxs-lookup"><span data-stu-id="cca5d-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="cca5d-110">Veri türü: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="cca5d-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="cca5d-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cca5d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cca5d-112">Bağlantı havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="cca5d-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="cca5d-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="cca5d-113">ListenBacklog</span></span>  
 <span data-ttu-id="cca5d-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cca5d-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="cca5d-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cca5d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cca5d-116">Bekleyen sıraya alınan bağlantı isteklerini maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="cca5d-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="cca5d-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="cca5d-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="cca5d-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cca5d-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="cca5d-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cca5d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cca5d-120">TCP bağlantı noktası paylaşma Bu bağlantı için etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cca5d-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="cca5d-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="cca5d-121">TeredoEnabled</span></span>  
 <span data-ttu-id="cca5d-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="cca5d-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="cca5d-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cca5d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cca5d-124">Teredo (güvenlik duvarının arkasındaki adresleme istemciler için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cca5d-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cca5d-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cca5d-125">Requirements</span></span>  
  
|<span data-ttu-id="cca5d-126">MOF</span><span class="sxs-lookup"><span data-stu-id="cca5d-126">MOF</span></span>|<span data-ttu-id="cca5d-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cca5d-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cca5d-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cca5d-128">Namespace</span></span>|<span data-ttu-id="cca5d-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cca5d-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cca5d-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cca5d-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
