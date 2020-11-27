---
title: Kanal sınıfı
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: a920636e7df9609b12834366b1488c80122f9fca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274237"
---
# <a name="channel-class"></a><span data-ttu-id="93142-102">Kanal sınıfı</span><span class="sxs-lookup"><span data-stu-id="93142-102">Channel class</span></span>

<span data-ttu-id="93142-103">Kanal</span><span class="sxs-lookup"><span data-stu-id="93142-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93142-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="93142-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="93142-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="93142-105">Methods</span></span>  

 <span data-ttu-id="93142-106">Kanal sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="93142-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="93142-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="93142-107">Properties</span></span>  

 <span data-ttu-id="93142-108">Kanal sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="93142-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="93142-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="93142-109">LocalAddress</span></span>  

 <span data-ttu-id="93142-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="93142-110">Data type: string</span></span>  
  
 <span data-ttu-id="93142-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="93142-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93142-112">Kanal için Yerel uç nokta.</span><span class="sxs-lookup"><span data-stu-id="93142-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="93142-113">ref</span><span class="sxs-lookup"><span data-stu-id="93142-113">ref</span></span>  

 <span data-ttu-id="93142-114">Veri türü: uç nokta</span><span class="sxs-lookup"><span data-stu-id="93142-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="93142-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="93142-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93142-116">Kanalın bağlandığı uç noktaya başvuru.</span><span class="sxs-lookup"><span data-stu-id="93142-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="93142-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="93142-117">RemoteAddress</span></span>  

 <span data-ttu-id="93142-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="93142-118">Data type: string</span></span>  
  
 <span data-ttu-id="93142-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="93142-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93142-120">Kanalla ilişkilendirilen uzak adres.</span><span class="sxs-lookup"><span data-stu-id="93142-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="93142-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="93142-121">SessionId</span></span>  

 <span data-ttu-id="93142-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="93142-122">Data type: string</span></span>  
  
 <span data-ttu-id="93142-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="93142-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93142-124">Varsa, geçerli oturum kimliği.</span><span class="sxs-lookup"><span data-stu-id="93142-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="93142-125">Tür</span><span class="sxs-lookup"><span data-stu-id="93142-125">Type</span></span>  

 <span data-ttu-id="93142-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="93142-126">Data type: string</span></span>  
  
 <span data-ttu-id="93142-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="93142-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93142-128">Kanalın türü.</span><span class="sxs-lookup"><span data-stu-id="93142-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93142-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93142-129">Requirements</span></span>  
  
|<span data-ttu-id="93142-130">MOF</span><span class="sxs-lookup"><span data-stu-id="93142-130">MOF</span></span>|<span data-ttu-id="93142-131">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="93142-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="93142-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="93142-132">Namespace</span></span>|<span data-ttu-id="93142-133">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="93142-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93142-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93142-134">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
