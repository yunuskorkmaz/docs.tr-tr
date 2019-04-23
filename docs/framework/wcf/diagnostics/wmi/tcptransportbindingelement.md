---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 6d2717bc2d1d14e369af2b9c5a8c0affb67501d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979244"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="b057f-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b057f-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="b057f-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b057f-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b057f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b057f-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b057f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b057f-105">Methods</span></span>  
 <span data-ttu-id="b057f-106">TcpTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b057f-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b057f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b057f-107">Properties</span></span>  
 <span data-ttu-id="b057f-108">TcpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b057f-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="b057f-109">Tcptransport</span><span class="sxs-lookup"><span data-stu-id="b057f-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="b057f-110">Veri türü: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b057f-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="b057f-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b057f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b057f-112">Bağlantı havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="b057f-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="b057f-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="b057f-113">ListenBacklog</span></span>  
 <span data-ttu-id="b057f-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="b057f-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b057f-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b057f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b057f-116">Bekleyen sıraya alınan bağlantı isteklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="b057f-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="b057f-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="b057f-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="b057f-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b057f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b057f-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b057f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b057f-120">Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b057f-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="b057f-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="b057f-121">TeredoEnabled</span></span>  
 <span data-ttu-id="b057f-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b057f-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="b057f-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b057f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b057f-124">Teredo (güvenlik duvarının arkasındaki istemcilere için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="b057f-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b057f-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b057f-125">Requirements</span></span>  
  
|<span data-ttu-id="b057f-126">MOF</span><span class="sxs-lookup"><span data-stu-id="b057f-126">MOF</span></span>|<span data-ttu-id="b057f-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b057f-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b057f-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b057f-128">Namespace</span></span>|<span data-ttu-id="b057f-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b057f-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b057f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b057f-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
