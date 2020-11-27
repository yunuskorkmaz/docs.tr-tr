---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: de00cac851e4c6d0fd6df16f3a01b65bb5f43415
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294683"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="1e3c6-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="1e3c6-102">TcpConnectionPoolSettings</span></span>

<span data-ttu-id="1e3c6-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="1e3c6-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e3c6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="1e3c6-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1e3c6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1e3c6-105">Methods</span></span>  

 <span data-ttu-id="1e3c6-106">TcpConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="1e3c6-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1e3c6-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1e3c6-107">Properties</span></span>  

 <span data-ttu-id="1e3c6-108">TcpConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="1e3c6-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="1e3c6-109">Adýdýr</span><span class="sxs-lookup"><span data-stu-id="1e3c6-109">GroupName</span></span>  

 <span data-ttu-id="1e3c6-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="1e3c6-110">Data type: string</span></span>  
  
 <span data-ttu-id="1e3c6-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1e3c6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e3c6-112">Bağlama öğesi tarafından kullanılan bağlantı havuzunun grup adı.</span><span class="sxs-lookup"><span data-stu-id="1e3c6-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="1e3c6-113">Timeout</span><span class="sxs-lookup"><span data-stu-id="1e3c6-113">IdleTimeout</span></span>  

 <span data-ttu-id="1e3c6-114">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="1e3c6-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="1e3c6-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1e3c6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e3c6-116">Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="1e3c6-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="1e3c6-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="1e3c6-117">LeaseTimeout</span></span>  

 <span data-ttu-id="1e3c6-118">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="1e3c6-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="1e3c6-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1e3c6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e3c6-120">Zaman aşımından önce kira işleminin tamamlanacağı en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="1e3c6-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="1e3c6-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="1e3c6-121">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="1e3c6-122">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="1e3c6-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="1e3c6-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="1e3c6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1e3c6-124">Her bitiş noktası için giden bağlantı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="1e3c6-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e3c6-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e3c6-125">Requirements</span></span>  
  
|<span data-ttu-id="1e3c6-126">MOF</span><span class="sxs-lookup"><span data-stu-id="1e3c6-126">MOF</span></span>|<span data-ttu-id="1e3c6-127">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1e3c6-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1e3c6-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="1e3c6-128">Namespace</span></span>|<span data-ttu-id="1e3c6-129">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="1e3c6-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e3c6-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e3c6-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
