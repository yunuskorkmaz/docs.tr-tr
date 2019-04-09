---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8c2d4bfc08a503a8d6eb0e8abf6f1e798b90bc83
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59095340"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="11a16-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="11a16-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="11a16-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="11a16-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a16-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11a16-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="11a16-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="11a16-105">Methods</span></span>  
 <span data-ttu-id="11a16-106">NamedPipeConnectionPoolSettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="11a16-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="11a16-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="11a16-107">Properties</span></span>  
 <span data-ttu-id="11a16-108">NamedPipeConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="11a16-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="11a16-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="11a16-109">GroupName</span></span>  
 <span data-ttu-id="11a16-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="11a16-110">Data type: string</span></span>  
  
 <span data-ttu-id="11a16-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="11a16-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11a16-112">Bağlama öğesi tarafından kullanılan bağlantı havuzunu grup adı.</span><span class="sxs-lookup"><span data-stu-id="11a16-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="11a16-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="11a16-113">IdleTimeout</span></span>  
 <span data-ttu-id="11a16-114">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="11a16-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="11a16-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="11a16-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11a16-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="11a16-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="11a16-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="11a16-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="11a16-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="11a16-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="11a16-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="11a16-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="11a16-120">Giden bağlantılar için istemci üzerindeki her bir uç nokta sayısı.</span><span class="sxs-lookup"><span data-stu-id="11a16-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11a16-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="11a16-121">Requirements</span></span>  
  
|<span data-ttu-id="11a16-122">MOF</span><span class="sxs-lookup"><span data-stu-id="11a16-122">MOF</span></span>|<span data-ttu-id="11a16-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="11a16-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="11a16-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="11a16-124">Namespace</span></span>|<span data-ttu-id="11a16-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="11a16-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11a16-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11a16-126">See also</span></span>

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
