---
title: "Kanal sınıfı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 93632d6a178c0f58143fc148a0e1eb51be94ed17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="channel-class"></a><span data-ttu-id="a14cb-102">Kanal sınıfı</span><span class="sxs-lookup"><span data-stu-id="a14cb-102">Channel class</span></span>
<span data-ttu-id="a14cb-103">Kanal</span><span class="sxs-lookup"><span data-stu-id="a14cb-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a14cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a14cb-104">Syntax</span></span>  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a14cb-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a14cb-105">Methods</span></span>  
 <span data-ttu-id="a14cb-106">Kanal sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="a14cb-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a14cb-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a14cb-107">Properties</span></span>  
 <span data-ttu-id="a14cb-108">Kanal sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a14cb-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="a14cb-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="a14cb-109">LocalAddress</span></span>  
 <span data-ttu-id="a14cb-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a14cb-110">Data type: string</span></span>  
  
 <span data-ttu-id="a14cb-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a14cb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a14cb-112">Kanalı yerel uç nokta.</span><span class="sxs-lookup"><span data-stu-id="a14cb-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="a14cb-113">ref</span><span class="sxs-lookup"><span data-stu-id="a14cb-113">ref</span></span>  
 <span data-ttu-id="a14cb-114">Veri türü: uç noktası</span><span class="sxs-lookup"><span data-stu-id="a14cb-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="a14cb-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a14cb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a14cb-116">Uç nokta kanal başvuru bağlanır.</span><span class="sxs-lookup"><span data-stu-id="a14cb-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="a14cb-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="a14cb-117">RemoteAddress</span></span>  
 <span data-ttu-id="a14cb-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a14cb-118">Data type: string</span></span>  
  
 <span data-ttu-id="a14cb-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a14cb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a14cb-120">Kanal ile ilişkilendirilen uzak adres.</span><span class="sxs-lookup"><span data-stu-id="a14cb-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="a14cb-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="a14cb-121">SessionId</span></span>  
 <span data-ttu-id="a14cb-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a14cb-122">Data type: string</span></span>  
  
 <span data-ttu-id="a14cb-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a14cb-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a14cb-124">Geçerli oturum kimliği, varsa.</span><span class="sxs-lookup"><span data-stu-id="a14cb-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="a14cb-125">Tür</span><span class="sxs-lookup"><span data-stu-id="a14cb-125">Type</span></span>  
 <span data-ttu-id="a14cb-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="a14cb-126">Data type: string</span></span>  
  
 <span data-ttu-id="a14cb-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="a14cb-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a14cb-128">Kanal türü.</span><span class="sxs-lookup"><span data-stu-id="a14cb-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a14cb-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a14cb-129">Requirements</span></span>  
  
|<span data-ttu-id="a14cb-130">MOF</span><span class="sxs-lookup"><span data-stu-id="a14cb-130">MOF</span></span>|<span data-ttu-id="a14cb-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a14cb-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a14cb-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="a14cb-132">Namespace</span></span>|<span data-ttu-id="a14cb-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a14cb-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a14cb-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a14cb-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
