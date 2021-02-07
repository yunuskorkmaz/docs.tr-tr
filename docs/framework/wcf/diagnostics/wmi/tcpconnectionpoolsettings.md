---
description: 'Bu konuda daha fazla bilgi edinin: TcpConnectionPoolSettings'
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 927fcba7f94bcbfa80e06479e79bf20986a661e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99715203"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="3a0b6-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3a0b6-103">TcpConnectionPoolSettings</span></span>

<span data-ttu-id="3a0b6-104">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3a0b6-104">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a0b6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3a0b6-105">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3a0b6-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3a0b6-106">Methods</span></span>  

 <span data-ttu-id="3a0b6-107">TcpConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="3a0b6-107">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3a0b6-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3a0b6-108">Properties</span></span>  

 <span data-ttu-id="3a0b6-109">TcpConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="3a0b6-109">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="3a0b6-110">Adýdýr</span><span class="sxs-lookup"><span data-stu-id="3a0b6-110">GroupName</span></span>  

 <span data-ttu-id="3a0b6-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="3a0b6-111">Data type: string</span></span>  
  
 <span data-ttu-id="3a0b6-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3a0b6-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a0b6-113">Bağlama öğesi tarafından kullanılan bağlantı havuzunun grup adı.</span><span class="sxs-lookup"><span data-stu-id="3a0b6-113">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="3a0b6-114">Timeout</span><span class="sxs-lookup"><span data-stu-id="3a0b6-114">IdleTimeout</span></span>  

 <span data-ttu-id="3a0b6-115">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="3a0b6-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="3a0b6-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3a0b6-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a0b6-117">Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="3a0b6-117">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="3a0b6-118">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="3a0b6-118">LeaseTimeout</span></span>  

 <span data-ttu-id="3a0b6-119">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="3a0b6-119">Data type: datetime</span></span>  
  
 <span data-ttu-id="3a0b6-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3a0b6-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a0b6-121">Zaman aşımından önce kira işleminin tamamlanacağı en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="3a0b6-121">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="3a0b6-122">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="3a0b6-122">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="3a0b6-123">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="3a0b6-123">Data type: sint32</span></span>  
  
 <span data-ttu-id="3a0b6-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="3a0b6-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a0b6-125">Her bitiş noktası için giden bağlantı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="3a0b6-125">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a0b6-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a0b6-126">Requirements</span></span>  
  
|<span data-ttu-id="3a0b6-127">MOF</span><span class="sxs-lookup"><span data-stu-id="3a0b6-127">MOF</span></span>|<span data-ttu-id="3a0b6-128">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3a0b6-128">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3a0b6-129">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="3a0b6-129">Namespace</span></span>|<span data-ttu-id="3a0b6-130">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="3a0b6-130">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a0b6-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a0b6-131">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
