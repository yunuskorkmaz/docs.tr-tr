---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8422e1adf9a8914b631431eba5c9c0ed058cd0f3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258029"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="04857-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="04857-102">NamedPipeConnectionPoolSettings</span></span>

<span data-ttu-id="04857-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="04857-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04857-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="04857-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="04857-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="04857-105">Methods</span></span>  

 <span data-ttu-id="04857-106">NamedPipeConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="04857-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="04857-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="04857-107">Properties</span></span>  

 <span data-ttu-id="04857-108">NamedPipeConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="04857-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="04857-109">Adýdýr</span><span class="sxs-lookup"><span data-stu-id="04857-109">GroupName</span></span>  

 <span data-ttu-id="04857-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="04857-110">Data type: string</span></span>  
  
 <span data-ttu-id="04857-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="04857-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04857-112">Bağlama öğesi tarafından kullanılan bağlantı havuzunun grup adı.</span><span class="sxs-lookup"><span data-stu-id="04857-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="04857-113">Timeout</span><span class="sxs-lookup"><span data-stu-id="04857-113">IdleTimeout</span></span>  

 <span data-ttu-id="04857-114">Veri türü: DateTime</span><span class="sxs-lookup"><span data-stu-id="04857-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="04857-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="04857-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04857-116">Bağlantı kesilmeden önce bağlantının boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="04857-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="04857-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="04857-117">MaxOutboundConnectionsPerEndpoint</span></span>  

 <span data-ttu-id="04857-118">Veri türü: Sint32</span><span class="sxs-lookup"><span data-stu-id="04857-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="04857-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="04857-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04857-120">İstemcideki her bir uç nokta için giden bağlantı sayısı üst sınırı.</span><span class="sxs-lookup"><span data-stu-id="04857-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04857-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04857-121">Requirements</span></span>  
  
|<span data-ttu-id="04857-122">MOF</span><span class="sxs-lookup"><span data-stu-id="04857-122">MOF</span></span>|<span data-ttu-id="04857-123">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="04857-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="04857-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="04857-124">Namespace</span></span>|<span data-ttu-id="04857-125">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="04857-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04857-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04857-126">See also</span></span>

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
