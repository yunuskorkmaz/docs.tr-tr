---
title: NamedPipeConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18740c4c87aaeafcd0a28991376e0c45fe688223
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="cdf54-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="cdf54-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="cdf54-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="cdf54-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdf54-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdf54-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cdf54-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cdf54-105">Methods</span></span>  
 <span data-ttu-id="cdf54-106">NamedPipeConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="cdf54-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cdf54-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cdf54-107">Properties</span></span>  
 <span data-ttu-id="cdf54-108">NamedPipeConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cdf54-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="cdf54-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="cdf54-109">GroupName</span></span>  
 <span data-ttu-id="cdf54-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cdf54-110">Data type: string</span></span>  
  
 <span data-ttu-id="cdf54-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cdf54-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cdf54-112">Bağlama öğesi tarafından kullanılan bağlantı havuzu grup adı.</span><span class="sxs-lookup"><span data-stu-id="cdf54-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="cdf54-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="cdf54-113">IdleTimeout</span></span>  
 <span data-ttu-id="cdf54-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="cdf54-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="cdf54-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cdf54-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cdf54-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="cdf54-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="cdf54-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="cdf54-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="cdf54-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cdf54-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="cdf54-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cdf54-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cdf54-120">İstemci üzerindeki her bitiş noktasıyla ilgili giden bağlantılar maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="cdf54-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdf54-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdf54-121">Requirements</span></span>  
  
|<span data-ttu-id="cdf54-122">MOF</span><span class="sxs-lookup"><span data-stu-id="cdf54-122">MOF</span></span>|<span data-ttu-id="cdf54-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cdf54-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cdf54-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cdf54-124">Namespace</span></span>|<span data-ttu-id="cdf54-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cdf54-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cdf54-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cdf54-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
