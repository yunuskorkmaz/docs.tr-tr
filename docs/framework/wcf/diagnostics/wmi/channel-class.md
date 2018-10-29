---
title: Kanal sınıfı
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 108d5f8e3cd092863dbd48e2bb9d180798b091a4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197879"
---
# <a name="channel-class"></a><span data-ttu-id="f350a-102">Kanal sınıfı</span><span class="sxs-lookup"><span data-stu-id="f350a-102">Channel class</span></span>
<span data-ttu-id="f350a-103">Kanal</span><span class="sxs-lookup"><span data-stu-id="f350a-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f350a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f350a-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f350a-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f350a-105">Methods</span></span>  
 <span data-ttu-id="f350a-106">Kanal sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="f350a-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f350a-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f350a-107">Properties</span></span>  
 <span data-ttu-id="f350a-108">Kanal sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="f350a-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="f350a-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="f350a-109">LocalAddress</span></span>  
 <span data-ttu-id="f350a-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f350a-110">Data type: string</span></span>  
  
 <span data-ttu-id="f350a-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f350a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f350a-112">Kanal için yerel uç nokta.</span><span class="sxs-lookup"><span data-stu-id="f350a-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="f350a-113">ref</span><span class="sxs-lookup"><span data-stu-id="f350a-113">ref</span></span>  
 <span data-ttu-id="f350a-114">Veri türü: uç nokta</span><span class="sxs-lookup"><span data-stu-id="f350a-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="f350a-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f350a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f350a-116">Bir başvuru kanal uç noktasına bağlanır.</span><span class="sxs-lookup"><span data-stu-id="f350a-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="f350a-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="f350a-117">RemoteAddress</span></span>  
 <span data-ttu-id="f350a-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f350a-118">Data type: string</span></span>  
  
 <span data-ttu-id="f350a-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f350a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f350a-120">Kanal ile ilişkilendirilen uzak adres.</span><span class="sxs-lookup"><span data-stu-id="f350a-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="f350a-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="f350a-121">SessionId</span></span>  
 <span data-ttu-id="f350a-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f350a-122">Data type: string</span></span>  
  
 <span data-ttu-id="f350a-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f350a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f350a-124">Geçerli oturum kimliği, varsa.</span><span class="sxs-lookup"><span data-stu-id="f350a-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="f350a-125">Tür</span><span class="sxs-lookup"><span data-stu-id="f350a-125">Type</span></span>  
 <span data-ttu-id="f350a-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="f350a-126">Data type: string</span></span>  
  
 <span data-ttu-id="f350a-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="f350a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f350a-128">Kanal türü.</span><span class="sxs-lookup"><span data-stu-id="f350a-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f350a-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f350a-129">Requirements</span></span>  
  
|<span data-ttu-id="f350a-130">MOF</span><span class="sxs-lookup"><span data-stu-id="f350a-130">MOF</span></span>|<span data-ttu-id="f350a-131">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f350a-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f350a-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="f350a-132">Namespace</span></span>|<span data-ttu-id="f350a-133">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f350a-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f350a-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f350a-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
