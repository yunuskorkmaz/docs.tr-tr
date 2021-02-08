---
description: 'Daha fazla bilgi edinin: NamedPipeConnectionPoolSettings'
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8d724c7a24f62a8d48797125528eb8a194ece660
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803119"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="a13ce-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a13ce-103">NamedPipeConnectionPoolSettings</span></span>

<span data-ttu-id="a13ce-104">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a13ce-104">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a13ce-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a13ce-105">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a13ce-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a13ce-106">Methods</span></span>  

 <span data-ttu-id="a13ce-107">NamedPipeConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="a13ce-107">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a13ce-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a13ce-108">Properties</span></span>  

 <span data-ttu-id="a13ce-109">NamedPipeConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="a13ce-109">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="a13ce-110">Adýdýr</span><span class="sxs-lookup"><span data-stu-id="a13ce-110">GroupName</span></span>  

 <span data-ttu-id="a13ce-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a13ce-111">Data type: string</span></span>  
  
 <span data-ttu-id="a13ce-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a13ce-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a13ce-113">Bağlama öğesi tarafından kullanılan bağlantı havuzunun grup adı.</span><span class="sxs-lookup"><span data-stu-id="a13ce-113">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="a13ce-114">Timeout</span><span class="sxs-lookup"><span data-stu-id="a13ce-114">IdleTimeout</span></span>  

 <span data-ttu-id="a13ce-115">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="a13ce-115">Data type: datetime</span></span>  
  
 <span data-ttu-id="a13ce-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a13ce-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a13ce-117">Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="a13ce-117">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="a13ce-118">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="a13ce-118">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="a13ce-119">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="a13ce-119">Data type: sint32</span></span>  
  
 <span data-ttu-id="a13ce-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="a13ce-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a13ce-121">İstemcideki her bir uç nokta için giden bağlantı sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="a13ce-121">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a13ce-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a13ce-122">Requirements</span></span>  
  
|<span data-ttu-id="a13ce-123">MOF</span><span class="sxs-lookup"><span data-stu-id="a13ce-123">MOF</span></span>|<span data-ttu-id="a13ce-124">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a13ce-124">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a13ce-125">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a13ce-125">Namespace</span></span>|<span data-ttu-id="a13ce-126">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="a13ce-126">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a13ce-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a13ce-127">See also</span></span>

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
