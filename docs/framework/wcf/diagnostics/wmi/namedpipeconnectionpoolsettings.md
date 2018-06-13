---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 3548a1f19672a98ad0fc81eec15d5be29e5170bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486292"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="669e9-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="669e9-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="669e9-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="669e9-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="669e9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="669e9-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="669e9-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="669e9-105">Methods</span></span>  
 <span data-ttu-id="669e9-106">NamedPipeConnectionPoolSettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="669e9-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="669e9-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="669e9-107">Properties</span></span>  
 <span data-ttu-id="669e9-108">NamedPipeConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="669e9-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="669e9-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="669e9-109">GroupName</span></span>  
 <span data-ttu-id="669e9-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="669e9-110">Data type: string</span></span>  
  
 <span data-ttu-id="669e9-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="669e9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="669e9-112">Bağlama öğesi tarafından kullanılan bağlantı havuzu grup adı.</span><span class="sxs-lookup"><span data-stu-id="669e9-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="669e9-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="669e9-113">IdleTimeout</span></span>  
 <span data-ttu-id="669e9-114">Veri türü: datetime</span><span class="sxs-lookup"><span data-stu-id="669e9-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="669e9-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="669e9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="669e9-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="669e9-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="669e9-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="669e9-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="669e9-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="669e9-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="669e9-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="669e9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="669e9-120">İstemci üzerindeki her bitiş noktasıyla ilgili giden bağlantılar maksimum sayısı.</span><span class="sxs-lookup"><span data-stu-id="669e9-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="669e9-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="669e9-121">Requirements</span></span>  
  
|<span data-ttu-id="669e9-122">MOF</span><span class="sxs-lookup"><span data-stu-id="669e9-122">MOF</span></span>|<span data-ttu-id="669e9-123">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="669e9-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="669e9-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="669e9-124">Namespace</span></span>|<span data-ttu-id="669e9-125">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="669e9-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="669e9-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="669e9-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
