---
title: Kanal sınıfı
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: f60a3946617b0994db1ba9e9ddf43be863be81f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59767454"
---
# <a name="channel-class"></a><span data-ttu-id="e62f4-102">Kanal sınıfı</span><span class="sxs-lookup"><span data-stu-id="e62f4-102">Channel class</span></span>
<span data-ttu-id="e62f4-103">Kanal</span><span class="sxs-lookup"><span data-stu-id="e62f4-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e62f4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e62f4-104">Syntax</span></span>  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e62f4-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e62f4-105">Methods</span></span>  
 <span data-ttu-id="e62f4-106">Kanal sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e62f4-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e62f4-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e62f4-107">Properties</span></span>  
 <span data-ttu-id="e62f4-108">Kanal sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e62f4-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="e62f4-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="e62f4-109">LocalAddress</span></span>  
 <span data-ttu-id="e62f4-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e62f4-110">Data type: string</span></span>  
  
 <span data-ttu-id="e62f4-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e62f4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e62f4-112">Kanal için yerel uç nokta.</span><span class="sxs-lookup"><span data-stu-id="e62f4-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="e62f4-113">ref</span><span class="sxs-lookup"><span data-stu-id="e62f4-113">ref</span></span>  
 <span data-ttu-id="e62f4-114">Veri türü: Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="e62f4-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="e62f4-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e62f4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e62f4-116">Bir başvuru kanal uç noktasına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="e62f4-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="e62f4-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="e62f4-117">RemoteAddress</span></span>  
 <span data-ttu-id="e62f4-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e62f4-118">Data type: string</span></span>  
  
 <span data-ttu-id="e62f4-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e62f4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e62f4-120">Kanal ile ilişkilendirilen uzak adres.</span><span class="sxs-lookup"><span data-stu-id="e62f4-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="e62f4-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="e62f4-121">SessionId</span></span>  
 <span data-ttu-id="e62f4-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e62f4-122">Data type: string</span></span>  
  
 <span data-ttu-id="e62f4-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e62f4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e62f4-124">Geçerli oturum kimliği, varsa.</span><span class="sxs-lookup"><span data-stu-id="e62f4-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="e62f4-125">Tür</span><span class="sxs-lookup"><span data-stu-id="e62f4-125">Type</span></span>  
 <span data-ttu-id="e62f4-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="e62f4-126">Data type: string</span></span>  
  
 <span data-ttu-id="e62f4-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="e62f4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e62f4-128">Kanal türü.</span><span class="sxs-lookup"><span data-stu-id="e62f4-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e62f4-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e62f4-129">Requirements</span></span>  
  
|<span data-ttu-id="e62f4-130">MOF</span><span class="sxs-lookup"><span data-stu-id="e62f4-130">MOF</span></span>|<span data-ttu-id="e62f4-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e62f4-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e62f4-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e62f4-132">Namespace</span></span>|<span data-ttu-id="e62f4-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e62f4-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e62f4-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e62f4-134">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
