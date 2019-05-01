---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 6d2717bc2d1d14e369af2b9c5a8c0affb67501d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956552"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="9189c-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9189c-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="9189c-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9189c-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9189c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9189c-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9189c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9189c-105">Methods</span></span>  
 <span data-ttu-id="9189c-106">TcpTransportBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="9189c-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9189c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9189c-107">Properties</span></span>  
 <span data-ttu-id="9189c-108">TcpTransportBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="9189c-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="9189c-109">Tcptransport</span><span class="sxs-lookup"><span data-stu-id="9189c-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="9189c-110">Veri türü: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9189c-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="9189c-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9189c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9189c-112">Bağlantı havuzu ayarları.</span><span class="sxs-lookup"><span data-stu-id="9189c-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="9189c-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="9189c-113">ListenBacklog</span></span>  
 <span data-ttu-id="9189c-114">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="9189c-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="9189c-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9189c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9189c-116">Bekleyen sıraya alınan bağlantı isteklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="9189c-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="9189c-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="9189c-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="9189c-118">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9189c-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="9189c-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9189c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9189c-120">Bu bağlantı için TCP bağlantı noktası paylaşımının etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="9189c-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="9189c-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="9189c-121">TeredoEnabled</span></span>  
 <span data-ttu-id="9189c-122">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="9189c-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="9189c-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="9189c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9189c-124">Teredo (güvenlik duvarının arkasındaki istemcilere için bir teknoloji) etkin olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="9189c-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9189c-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9189c-125">Requirements</span></span>  
  
|<span data-ttu-id="9189c-126">MOF</span><span class="sxs-lookup"><span data-stu-id="9189c-126">MOF</span></span>|<span data-ttu-id="9189c-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9189c-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9189c-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="9189c-128">Namespace</span></span>|<span data-ttu-id="9189c-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9189c-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9189c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9189c-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
