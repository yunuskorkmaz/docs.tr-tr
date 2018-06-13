---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: e64f689923d95546c8cecdf47c247faf79242ebf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485838"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="59247-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="59247-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="59247-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="59247-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59247-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="59247-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="59247-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="59247-105">Methods</span></span>  
 <span data-ttu-id="59247-106">TcpTransportBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="59247-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="59247-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="59247-107">Properties</span></span>  
 <span data-ttu-id="59247-108">TcpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="59247-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="59247-109">Tcptransport</span><span class="sxs-lookup"><span data-stu-id="59247-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="59247-110">Veri türü: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="59247-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="59247-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="59247-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59247-112">Bağlantı havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="59247-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="59247-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="59247-113">ListenBacklog</span></span>  
 <span data-ttu-id="59247-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="59247-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="59247-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="59247-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59247-116">Bekleyen sıraya alınan bağlantı isteklerini maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="59247-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="59247-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="59247-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="59247-118">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="59247-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="59247-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="59247-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59247-120">TCP bağlantı noktası paylaşma Bu bağlantı için etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="59247-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="59247-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="59247-121">TeredoEnabled</span></span>  
 <span data-ttu-id="59247-122">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="59247-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="59247-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="59247-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="59247-124">Teredo (güvenlik duvarının arkasındaki adresleme istemciler için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="59247-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59247-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="59247-125">Requirements</span></span>  
  
|<span data-ttu-id="59247-126">MOF</span><span class="sxs-lookup"><span data-stu-id="59247-126">MOF</span></span>|<span data-ttu-id="59247-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="59247-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="59247-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="59247-128">Namespace</span></span>|<span data-ttu-id="59247-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="59247-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59247-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59247-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
