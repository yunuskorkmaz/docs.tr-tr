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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cf9c39334289cb30d1a01917c0be37da02fcdc5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="62604-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="62604-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="62604-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="62604-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62604-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62604-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="62604-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="62604-105">Methods</span></span>  
 <span data-ttu-id="62604-106">NamedPipeConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="62604-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="62604-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="62604-107">Properties</span></span>  
 <span data-ttu-id="62604-108">NamedPipeConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="62604-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="62604-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="62604-109">GroupName</span></span>  
 <span data-ttu-id="62604-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="62604-110">Data type: string</span></span>  
  
 <span data-ttu-id="62604-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="62604-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62604-112">Bağlama öğesi tarafından kullanılan bağlantı havuzu grup adı.</span><span class="sxs-lookup"><span data-stu-id="62604-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="62604-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="62604-113">IdleTimeout</span></span>  
 <span data-ttu-id="62604-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="62604-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="62604-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="62604-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62604-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="62604-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="62604-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="62604-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="62604-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="62604-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="62604-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="62604-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="62604-120">İstemci üzerindeki her bitiş noktasıyla ilgili giden bağlantılar maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="62604-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62604-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62604-121">Requirements</span></span>  
  
|<span data-ttu-id="62604-122">MOF</span><span class="sxs-lookup"><span data-stu-id="62604-122">MOF</span></span>|<span data-ttu-id="62604-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="62604-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="62604-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="62604-124">Namespace</span></span>|<span data-ttu-id="62604-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="62604-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62604-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62604-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
