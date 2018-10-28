---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 77d8403947d341ea2efcef98bbf166f94f75f31f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188735"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="cb963-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="cb963-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="cb963-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="cb963-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb963-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb963-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cb963-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cb963-105">Methods</span></span>  
 <span data-ttu-id="cb963-106">NamedPipeConnectionPoolSettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="cb963-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cb963-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cb963-107">Properties</span></span>  
 <span data-ttu-id="cb963-108">NamedPipeConnectionPoolSettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cb963-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="cb963-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="cb963-109">GroupName</span></span>  
 <span data-ttu-id="cb963-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cb963-110">Data type: string</span></span>  
  
 <span data-ttu-id="cb963-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cb963-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb963-112">Bağlama öğesi tarafından kullanılan bağlantı havuzunu grup adı.</span><span class="sxs-lookup"><span data-stu-id="cb963-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="cb963-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="cb963-113">IdleTimeout</span></span>  
 <span data-ttu-id="cb963-114">Veri türü: tarih/saat</span><span class="sxs-lookup"><span data-stu-id="cb963-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="cb963-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cb963-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb963-116">Bağlantı kesilmeden önce boşta kalabileceği en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="cb963-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="cb963-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="cb963-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="cb963-118">Veri türü: SINT32</span><span class="sxs-lookup"><span data-stu-id="cb963-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="cb963-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cb963-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb963-120">Giden bağlantılar için istemci üzerindeki her bir uç nokta sayısı.</span><span class="sxs-lookup"><span data-stu-id="cb963-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb963-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb963-121">Requirements</span></span>  
  
|<span data-ttu-id="cb963-122">MOF</span><span class="sxs-lookup"><span data-stu-id="cb963-122">MOF</span></span>|<span data-ttu-id="cb963-123">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cb963-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cb963-124">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cb963-124">Namespace</span></span>|<span data-ttu-id="cb963-125">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cb963-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb963-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb963-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
