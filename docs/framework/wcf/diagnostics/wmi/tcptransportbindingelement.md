---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 6af85d62fffada95537494692b8694f42d7a2932
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96290094"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="4464a-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4464a-102">TcpTransportBindingElement</span></span>

<span data-ttu-id="4464a-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4464a-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4464a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4464a-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4464a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4464a-105">Methods</span></span>  

 <span data-ttu-id="4464a-106">TcpTransportBindingElement Class herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="4464a-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4464a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4464a-107">Properties</span></span>  

 <span data-ttu-id="4464a-108">TcpTransportBindingElement class aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="4464a-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="4464a-109">NamedPipeTransport</span><span class="sxs-lookup"><span data-stu-id="4464a-109">ConnectionPoolSettings</span></span>  

 <span data-ttu-id="4464a-110">Veri türü: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4464a-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="4464a-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="4464a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4464a-112">Bağlantı havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="4464a-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="4464a-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="4464a-113">ListenBacklog</span></span>  

 <span data-ttu-id="4464a-114">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="4464a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4464a-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="4464a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4464a-116">Beklemede olabilecek en fazla sıraya alınmış bağlantı isteği sayısı.</span><span class="sxs-lookup"><span data-stu-id="4464a-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="4464a-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="4464a-117">PortSharingEnabled</span></span>  

 <span data-ttu-id="4464a-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="4464a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="4464a-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="4464a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4464a-120">Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boolean değer.</span><span class="sxs-lookup"><span data-stu-id="4464a-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="4464a-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="4464a-121">TeredoEnabled</span></span>  

 <span data-ttu-id="4464a-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="4464a-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="4464a-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="4464a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4464a-124">Teredo 'Nun (güvenlik duvarlarının arkasındaki istemcileri adresleme teknolojisinin) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="4464a-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4464a-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4464a-125">Requirements</span></span>  
  
|<span data-ttu-id="4464a-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4464a-126">MOF</span></span>|<span data-ttu-id="4464a-127">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="4464a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4464a-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="4464a-128">Namespace</span></span>|<span data-ttu-id="4464a-129">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="4464a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4464a-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4464a-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
