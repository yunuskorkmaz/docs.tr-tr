---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 0d5dc5c9b9bf2313d18c9fadb1a2adb87c1b11b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610792"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="16f36-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="16f36-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="16f36-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="16f36-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16f36-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16f36-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="16f36-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="16f36-105">Methods</span></span>  
 <span data-ttu-id="16f36-106">TcpTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="16f36-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="16f36-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="16f36-107">Properties</span></span>  
 <span data-ttu-id="16f36-108">TcpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="16f36-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="16f36-109">Tcptransport</span><span class="sxs-lookup"><span data-stu-id="16f36-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="16f36-110">Veri türü: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="16f36-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="16f36-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="16f36-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16f36-112">Bağlantı havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="16f36-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="16f36-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="16f36-113">ListenBacklog</span></span>  
 <span data-ttu-id="16f36-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="16f36-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="16f36-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="16f36-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16f36-116">Bekleyen sıraya alınan bağlantı isteklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="16f36-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="16f36-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="16f36-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="16f36-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="16f36-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="16f36-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="16f36-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16f36-120">Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="16f36-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="16f36-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="16f36-121">TeredoEnabled</span></span>  
 <span data-ttu-id="16f36-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="16f36-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="16f36-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="16f36-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16f36-124">Teredo (güvenlik duvarının arkasındaki istemcilere için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="16f36-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16f36-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16f36-125">Requirements</span></span>  
  
|<span data-ttu-id="16f36-126">MOF</span><span class="sxs-lookup"><span data-stu-id="16f36-126">MOF</span></span>|<span data-ttu-id="16f36-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="16f36-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="16f36-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="16f36-128">Namespace</span></span>|<span data-ttu-id="16f36-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="16f36-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16f36-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16f36-130">See also</span></span>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
