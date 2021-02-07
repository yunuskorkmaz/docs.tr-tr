---
description: 'Daha fazla bilgi edinin: Kanal sınıfı'
title: Kanal sınıfı
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: dcc92f78f09e9a73a24134c6c0685949f46f38dd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99757728"
---
# <a name="channel-class"></a><span data-ttu-id="b0312-103">Kanal sınıfı</span><span class="sxs-lookup"><span data-stu-id="b0312-103">Channel class</span></span>

<span data-ttu-id="b0312-104">Kanal</span><span class="sxs-lookup"><span data-stu-id="b0312-104">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0312-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b0312-105">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b0312-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b0312-106">Methods</span></span>  

 <span data-ttu-id="b0312-107">Kanal sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b0312-107">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b0312-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b0312-108">Properties</span></span>  

 <span data-ttu-id="b0312-109">Kanal sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b0312-109">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="b0312-110">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="b0312-110">LocalAddress</span></span>  

 <span data-ttu-id="b0312-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b0312-111">Data type: string</span></span>  
  
 <span data-ttu-id="b0312-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b0312-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0312-113">Kanal için Yerel uç nokta.</span><span class="sxs-lookup"><span data-stu-id="b0312-113">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="b0312-114">ref</span><span class="sxs-lookup"><span data-stu-id="b0312-114">ref</span></span>  

 <span data-ttu-id="b0312-115">Veri türü: uç nokta</span><span class="sxs-lookup"><span data-stu-id="b0312-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="b0312-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b0312-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0312-117">Kanalın bağlandığı uç noktaya başvuru.</span><span class="sxs-lookup"><span data-stu-id="b0312-117">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="b0312-118">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="b0312-118">RemoteAddress</span></span>  

 <span data-ttu-id="b0312-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b0312-119">Data type: string</span></span>  
  
 <span data-ttu-id="b0312-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b0312-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0312-121">Kanalla ilişkilendirilen uzak adres.</span><span class="sxs-lookup"><span data-stu-id="b0312-121">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="b0312-122">SessionId</span><span class="sxs-lookup"><span data-stu-id="b0312-122">SessionId</span></span>  

 <span data-ttu-id="b0312-123">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b0312-123">Data type: string</span></span>  
  
 <span data-ttu-id="b0312-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b0312-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0312-125">Varsa, geçerli oturum kimliği.</span><span class="sxs-lookup"><span data-stu-id="b0312-125">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="b0312-126">Tür</span><span class="sxs-lookup"><span data-stu-id="b0312-126">Type</span></span>  

 <span data-ttu-id="b0312-127">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="b0312-127">Data type: string</span></span>  
  
 <span data-ttu-id="b0312-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="b0312-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0312-129">Kanalın türü.</span><span class="sxs-lookup"><span data-stu-id="b0312-129">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0312-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0312-130">Requirements</span></span>  
  
|<span data-ttu-id="b0312-131">MOF</span><span class="sxs-lookup"><span data-stu-id="b0312-131">MOF</span></span>|<span data-ttu-id="b0312-132">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b0312-132">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b0312-133">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b0312-133">Namespace</span></span>|<span data-ttu-id="b0312-134">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="b0312-134">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0312-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0312-135">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
