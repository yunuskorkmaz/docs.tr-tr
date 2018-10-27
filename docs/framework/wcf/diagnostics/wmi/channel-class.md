---
title: Kanal sınıfı
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 108d5f8e3cd092863dbd48e2bb9d180798b091a4
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50047377"
---
# <a name="channel-class"></a><span data-ttu-id="fb5bb-102">Kanal sınıfı</span><span class="sxs-lookup"><span data-stu-id="fb5bb-102">Channel class</span></span>
<span data-ttu-id="fb5bb-103">Kanal</span><span class="sxs-lookup"><span data-stu-id="fb5bb-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb5bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb5bb-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="fb5bb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fb5bb-105">Methods</span></span>  
 <span data-ttu-id="fb5bb-106">Kanal sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="fb5bb-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fb5bb-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="fb5bb-107">Properties</span></span>  
 <span data-ttu-id="fb5bb-108">Kanal sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fb5bb-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="fb5bb-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="fb5bb-109">LocalAddress</span></span>  
 <span data-ttu-id="fb5bb-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="fb5bb-110">Data type: string</span></span>  
  
 <span data-ttu-id="fb5bb-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="fb5bb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb5bb-112">Kanal için yerel uç nokta.</span><span class="sxs-lookup"><span data-stu-id="fb5bb-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="fb5bb-113">ref</span><span class="sxs-lookup"><span data-stu-id="fb5bb-113">ref</span></span>  
 <span data-ttu-id="fb5bb-114">Veri türü: uç nokta</span><span class="sxs-lookup"><span data-stu-id="fb5bb-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="fb5bb-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="fb5bb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb5bb-116">Bir başvuru kanal uç noktasına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="fb5bb-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="fb5bb-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="fb5bb-117">RemoteAddress</span></span>  
 <span data-ttu-id="fb5bb-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="fb5bb-118">Data type: string</span></span>  
  
 <span data-ttu-id="fb5bb-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="fb5bb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb5bb-120">Kanal ile ilişkilendirilen uzak adres.</span><span class="sxs-lookup"><span data-stu-id="fb5bb-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="fb5bb-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="fb5bb-121">SessionId</span></span>  
 <span data-ttu-id="fb5bb-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="fb5bb-122">Data type: string</span></span>  
  
 <span data-ttu-id="fb5bb-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="fb5bb-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb5bb-124">Geçerli oturum kimliği, varsa.</span><span class="sxs-lookup"><span data-stu-id="fb5bb-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="fb5bb-125">Tür</span><span class="sxs-lookup"><span data-stu-id="fb5bb-125">Type</span></span>  
 <span data-ttu-id="fb5bb-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="fb5bb-126">Data type: string</span></span>  
  
 <span data-ttu-id="fb5bb-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="fb5bb-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb5bb-128">Kanal türü.</span><span class="sxs-lookup"><span data-stu-id="fb5bb-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb5bb-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb5bb-129">Requirements</span></span>  
  
|<span data-ttu-id="fb5bb-130">MOF</span><span class="sxs-lookup"><span data-stu-id="fb5bb-130">MOF</span></span>|<span data-ttu-id="fb5bb-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fb5bb-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fb5bb-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="fb5bb-132">Namespace</span></span>|<span data-ttu-id="fb5bb-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fb5bb-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb5bb-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb5bb-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
