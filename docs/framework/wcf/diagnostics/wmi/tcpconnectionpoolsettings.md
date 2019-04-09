---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 6fa68eed241edaea40b66c31240a4201e05779f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093536"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="21d6c-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="21d6c-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="21d6c-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="21d6c-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21d6c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21d6c-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="21d6c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="21d6c-105">Methods</span></span>  
 <span data-ttu-id="21d6c-106">TcpConnectionPoolSettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="21d6c-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="21d6c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="21d6c-107">Properties</span></span>  
 <span data-ttu-id="21d6c-108">TcpConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="21d6c-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="21d6c-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="21d6c-109">GroupName</span></span>  
 <span data-ttu-id="21d6c-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="21d6c-110">Data type: string</span></span>  
  
 <span data-ttu-id="21d6c-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="21d6c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21d6c-112">Bağlama öğesi tarafından kullanılan bağlantı havuzunu grup adı.</span><span class="sxs-lookup"><span data-stu-id="21d6c-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="21d6c-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="21d6c-113">IdleTimeout</span></span>  
 <span data-ttu-id="21d6c-114">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="21d6c-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="21d6c-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="21d6c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21d6c-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="21d6c-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="21d6c-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="21d6c-117">LeaseTimeout</span></span>  
 <span data-ttu-id="21d6c-118">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="21d6c-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="21d6c-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="21d6c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21d6c-120">Kira işlemi zaman aşımına uğramadan önce tamamlanması için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="21d6c-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="21d6c-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="21d6c-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="21d6c-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="21d6c-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="21d6c-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="21d6c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21d6c-124">Her bir uç noktası için en fazla giden bağlantı.</span><span class="sxs-lookup"><span data-stu-id="21d6c-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21d6c-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21d6c-125">Requirements</span></span>  
  
|<span data-ttu-id="21d6c-126">MOF</span><span class="sxs-lookup"><span data-stu-id="21d6c-126">MOF</span></span>|<span data-ttu-id="21d6c-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="21d6c-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="21d6c-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="21d6c-128">Namespace</span></span>|<span data-ttu-id="21d6c-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="21d6c-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21d6c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21d6c-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
