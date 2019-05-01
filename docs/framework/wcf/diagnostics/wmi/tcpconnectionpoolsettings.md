---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 6fa68eed241edaea40b66c31240a4201e05779f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956583"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="426fe-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="426fe-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="426fe-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="426fe-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="426fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="426fe-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="426fe-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="426fe-105">Methods</span></span>  
 <span data-ttu-id="426fe-106">TcpConnectionPoolSettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="426fe-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="426fe-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="426fe-107">Properties</span></span>  
 <span data-ttu-id="426fe-108">TcpConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="426fe-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="426fe-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="426fe-109">GroupName</span></span>  
 <span data-ttu-id="426fe-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="426fe-110">Data type: string</span></span>  
  
 <span data-ttu-id="426fe-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="426fe-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="426fe-112">Bağlama öğesi tarafından kullanılan bağlantı havuzunu grup adı.</span><span class="sxs-lookup"><span data-stu-id="426fe-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="426fe-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="426fe-113">IdleTimeout</span></span>  
 <span data-ttu-id="426fe-114">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="426fe-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="426fe-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="426fe-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="426fe-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="426fe-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="426fe-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="426fe-117">LeaseTimeout</span></span>  
 <span data-ttu-id="426fe-118">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="426fe-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="426fe-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="426fe-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="426fe-120">Kira işlemi zaman aşımına uğramadan önce tamamlanması için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="426fe-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="426fe-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="426fe-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="426fe-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="426fe-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="426fe-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="426fe-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="426fe-124">Her bir uç noktası için en fazla giden bağlantı.</span><span class="sxs-lookup"><span data-stu-id="426fe-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="426fe-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="426fe-125">Requirements</span></span>  
  
|<span data-ttu-id="426fe-126">MOF</span><span class="sxs-lookup"><span data-stu-id="426fe-126">MOF</span></span>|<span data-ttu-id="426fe-127">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="426fe-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="426fe-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="426fe-128">Namespace</span></span>|<span data-ttu-id="426fe-129">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="426fe-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="426fe-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="426fe-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
