---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 3dddfa878e3cb5bd89fb76009d0dba530debb297
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725083"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="77d4b-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="77d4b-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="77d4b-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="77d4b-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77d4b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77d4b-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="77d4b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="77d4b-105">Methods</span></span>  
 <span data-ttu-id="77d4b-106">NamedPipeConnectionPoolSettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="77d4b-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="77d4b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="77d4b-107">Properties</span></span>  
 <span data-ttu-id="77d4b-108">NamedPipeConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="77d4b-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="77d4b-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="77d4b-109">GroupName</span></span>  
 <span data-ttu-id="77d4b-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="77d4b-110">Data type: string</span></span>  
  
 <span data-ttu-id="77d4b-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="77d4b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77d4b-112">Bağlama öğesi tarafından kullanılan bağlantı havuzunu grup adı.</span><span class="sxs-lookup"><span data-stu-id="77d4b-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="77d4b-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="77d4b-113">IdleTimeout</span></span>  
 <span data-ttu-id="77d4b-114">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="77d4b-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="77d4b-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="77d4b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77d4b-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="77d4b-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="77d4b-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="77d4b-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="77d4b-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="77d4b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="77d4b-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="77d4b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="77d4b-120">Giden bağlantılar için istemci üzerindeki her bir uç nokta sayısı.</span><span class="sxs-lookup"><span data-stu-id="77d4b-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77d4b-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77d4b-121">Requirements</span></span>  
  
|<span data-ttu-id="77d4b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="77d4b-122">MOF</span></span>|<span data-ttu-id="77d4b-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="77d4b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="77d4b-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="77d4b-124">Namespace</span></span>|<span data-ttu-id="77d4b-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="77d4b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77d4b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77d4b-126">See also</span></span>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
