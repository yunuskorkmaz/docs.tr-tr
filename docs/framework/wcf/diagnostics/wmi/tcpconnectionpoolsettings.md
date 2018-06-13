---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 4a30ad3ddfef5d39942345b0e0d5274eeff8e596
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485928"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="2d77a-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2d77a-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="2d77a-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2d77a-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d77a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d77a-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2d77a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2d77a-105">Methods</span></span>  
 <span data-ttu-id="2d77a-106">TcpConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="2d77a-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2d77a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2d77a-107">Properties</span></span>  
 <span data-ttu-id="2d77a-108">TcpConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2d77a-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="2d77a-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="2d77a-109">GroupName</span></span>  
 <span data-ttu-id="2d77a-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2d77a-110">Data type: string</span></span>  
  
 <span data-ttu-id="2d77a-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2d77a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2d77a-112">Bağlama öğesi tarafından kullanılan bağlantı havuzu grup adı.</span><span class="sxs-lookup"><span data-stu-id="2d77a-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="2d77a-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="2d77a-113">IdleTimeout</span></span>  
 <span data-ttu-id="2d77a-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="2d77a-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="2d77a-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2d77a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2d77a-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="2d77a-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="2d77a-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="2d77a-117">LeaseTimeout</span></span>  
 <span data-ttu-id="2d77a-118">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="2d77a-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="2d77a-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2d77a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2d77a-120">Zaman aşımından önce tamamlamak kira işlemi için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="2d77a-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="2d77a-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="2d77a-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="2d77a-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="2d77a-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="2d77a-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="2d77a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2d77a-124">Her uç nokta için en fazla giden bağlantı.</span><span class="sxs-lookup"><span data-stu-id="2d77a-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d77a-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d77a-125">Requirements</span></span>  
  
|<span data-ttu-id="2d77a-126">MOF</span><span class="sxs-lookup"><span data-stu-id="2d77a-126">MOF</span></span>|<span data-ttu-id="2d77a-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2d77a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2d77a-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2d77a-128">Namespace</span></span>|<span data-ttu-id="2d77a-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2d77a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d77a-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d77a-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
