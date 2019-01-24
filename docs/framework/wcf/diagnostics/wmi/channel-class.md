---
title: Kanal sınıfı
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 3fbf398cca7ae9adbbecb9439bf3cbd32eb03969
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668398"
---
# <a name="channel-class"></a><span data-ttu-id="14d42-102">Kanal sınıfı</span><span class="sxs-lookup"><span data-stu-id="14d42-102">Channel class</span></span>
<span data-ttu-id="14d42-103">Kanal</span><span class="sxs-lookup"><span data-stu-id="14d42-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14d42-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14d42-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="14d42-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="14d42-105">Methods</span></span>  
 <span data-ttu-id="14d42-106">Kanal sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="14d42-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="14d42-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="14d42-107">Properties</span></span>  
 <span data-ttu-id="14d42-108">Kanal sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="14d42-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="14d42-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="14d42-109">LocalAddress</span></span>  
 <span data-ttu-id="14d42-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="14d42-110">Data type: string</span></span>  
  
 <span data-ttu-id="14d42-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14d42-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14d42-112">Kanal için yerel uç nokta.</span><span class="sxs-lookup"><span data-stu-id="14d42-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="14d42-113">ref</span><span class="sxs-lookup"><span data-stu-id="14d42-113">ref</span></span>  
 <span data-ttu-id="14d42-114">Veri türü: Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="14d42-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="14d42-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14d42-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14d42-116">Bir başvuru kanal uç noktasına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="14d42-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="14d42-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="14d42-117">RemoteAddress</span></span>  
 <span data-ttu-id="14d42-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="14d42-118">Data type: string</span></span>  
  
 <span data-ttu-id="14d42-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14d42-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14d42-120">Kanal ile ilişkilendirilen uzak adres.</span><span class="sxs-lookup"><span data-stu-id="14d42-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="14d42-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="14d42-121">SessionId</span></span>  
 <span data-ttu-id="14d42-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="14d42-122">Data type: string</span></span>  
  
 <span data-ttu-id="14d42-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14d42-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14d42-124">Geçerli oturum kimliği, varsa.</span><span class="sxs-lookup"><span data-stu-id="14d42-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="14d42-125">Tür</span><span class="sxs-lookup"><span data-stu-id="14d42-125">Type</span></span>  
 <span data-ttu-id="14d42-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="14d42-126">Data type: string</span></span>  
  
 <span data-ttu-id="14d42-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14d42-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14d42-128">Kanal türü.</span><span class="sxs-lookup"><span data-stu-id="14d42-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14d42-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14d42-129">Requirements</span></span>  
  
|<span data-ttu-id="14d42-130">MOF</span><span class="sxs-lookup"><span data-stu-id="14d42-130">MOF</span></span>|<span data-ttu-id="14d42-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="14d42-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="14d42-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="14d42-132">Namespace</span></span>|<span data-ttu-id="14d42-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="14d42-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14d42-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14d42-134">See also</span></span>
- <xref:System.ServiceModel.Channels.ChannelBase>
