---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5038d093333eca9ca191c3ecae4cfa889d723276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="58bba-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="58bba-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="58bba-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="58bba-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58bba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58bba-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="58bba-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="58bba-105">Methods</span></span>  
 <span data-ttu-id="58bba-106">TcpConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="58bba-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="58bba-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="58bba-107">Properties</span></span>  
 <span data-ttu-id="58bba-108">TcpConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="58bba-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="58bba-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="58bba-109">GroupName</span></span>  
 <span data-ttu-id="58bba-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="58bba-110">Data type: string</span></span>  
  
 <span data-ttu-id="58bba-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="58bba-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="58bba-112">Bağlama öğesi tarafından kullanılan bağlantı havuzu grup adı.</span><span class="sxs-lookup"><span data-stu-id="58bba-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="58bba-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="58bba-113">IdleTimeout</span></span>  
 <span data-ttu-id="58bba-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="58bba-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="58bba-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="58bba-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="58bba-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="58bba-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="58bba-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="58bba-117">LeaseTimeout</span></span>  
 <span data-ttu-id="58bba-118">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="58bba-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="58bba-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="58bba-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="58bba-120">Zaman aşımından önce tamamlamak kira işlemi için en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="58bba-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="58bba-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="58bba-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="58bba-122">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="58bba-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="58bba-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="58bba-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="58bba-124">Her uç nokta için en fazla giden bağlantı.</span><span class="sxs-lookup"><span data-stu-id="58bba-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58bba-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58bba-125">Requirements</span></span>  
  
|<span data-ttu-id="58bba-126">MOF</span><span class="sxs-lookup"><span data-stu-id="58bba-126">MOF</span></span>|<span data-ttu-id="58bba-127">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="58bba-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="58bba-128">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="58bba-128">Namespace</span></span>|<span data-ttu-id="58bba-129">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="58bba-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="58bba-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58bba-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
