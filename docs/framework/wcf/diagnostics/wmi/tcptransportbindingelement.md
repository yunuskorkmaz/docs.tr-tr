---
description: 'Daha fazla bilgi edinin: TcpTransportBindingElement'
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: b52bb2eb4b40648808459f76e068a6f72f9476a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715151"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="97d82-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="97d82-103">TcpTransportBindingElement</span></span>

<span data-ttu-id="97d82-104">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="97d82-104">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d82-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="97d82-105">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="97d82-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="97d82-106">Methods</span></span>  

 <span data-ttu-id="97d82-107">TcpTransportBindingElement Class herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="97d82-107">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="97d82-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="97d82-108">Properties</span></span>  

 <span data-ttu-id="97d82-109">TcpTransportBindingElement class aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="97d82-109">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="97d82-110">NamedPipeTransport</span><span class="sxs-lookup"><span data-stu-id="97d82-110">ConnectionPoolSettings</span></span>  

 <span data-ttu-id="97d82-111">Veri türü: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="97d82-111">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="97d82-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="97d82-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="97d82-113">Bağlantı havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="97d82-113">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="97d82-114">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="97d82-114">ListenBacklog</span></span>  

 <span data-ttu-id="97d82-115">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="97d82-115">Data type: sint32</span></span>  
  
 <span data-ttu-id="97d82-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="97d82-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="97d82-117">Beklemede olabilecek en fazla sıraya alınmış bağlantı isteği sayısı.</span><span class="sxs-lookup"><span data-stu-id="97d82-117">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="97d82-118">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="97d82-118">PortSharingEnabled</span></span>  

 <span data-ttu-id="97d82-119">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="97d82-119">Data type: boolean</span></span>  
  
 <span data-ttu-id="97d82-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="97d82-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="97d82-121">Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="97d82-121">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="97d82-122">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="97d82-122">TeredoEnabled</span></span>  

 <span data-ttu-id="97d82-123">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="97d82-123">Data type: boolean</span></span>  
  
 <span data-ttu-id="97d82-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="97d82-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="97d82-125">Teredo 'Nun (güvenlik duvarlarının arkasındaki istemcileri adresleme teknolojisinin) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="97d82-125">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d82-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="97d82-126">Requirements</span></span>  
  
|<span data-ttu-id="97d82-127">MOF</span><span class="sxs-lookup"><span data-stu-id="97d82-127">MOF</span></span>|<span data-ttu-id="97d82-128">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="97d82-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="97d82-129">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="97d82-129">Namespace</span></span>|<span data-ttu-id="97d82-130">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="97d82-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="97d82-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97d82-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
