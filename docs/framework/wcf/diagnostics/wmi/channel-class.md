---
title: Kanal sınıfı
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 4b7c66560c0c136a258c527d8a681d491eb50aae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485833"
---
# <a name="channel-class"></a><span data-ttu-id="668ec-102">Kanal sınıfı</span><span class="sxs-lookup"><span data-stu-id="668ec-102">Channel class</span></span>
<span data-ttu-id="668ec-103">Kanal</span><span class="sxs-lookup"><span data-stu-id="668ec-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="668ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="668ec-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="668ec-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="668ec-105">Methods</span></span>  
 <span data-ttu-id="668ec-106">Kanal sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="668ec-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="668ec-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="668ec-107">Properties</span></span>  
 <span data-ttu-id="668ec-108">Kanal sınıfı aşağıdaki özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="668ec-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="668ec-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="668ec-109">LocalAddress</span></span>  
 <span data-ttu-id="668ec-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="668ec-110">Data type: string</span></span>  
  
 <span data-ttu-id="668ec-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="668ec-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="668ec-112">Kanalı yerel uç nokta.</span><span class="sxs-lookup"><span data-stu-id="668ec-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="668ec-113">ref</span><span class="sxs-lookup"><span data-stu-id="668ec-113">ref</span></span>  
 <span data-ttu-id="668ec-114">Veri türü: uç noktası</span><span class="sxs-lookup"><span data-stu-id="668ec-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="668ec-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="668ec-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="668ec-116">Uç nokta kanal başvuru bağlanır.</span><span class="sxs-lookup"><span data-stu-id="668ec-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="668ec-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="668ec-117">RemoteAddress</span></span>  
 <span data-ttu-id="668ec-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="668ec-118">Data type: string</span></span>  
  
 <span data-ttu-id="668ec-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="668ec-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="668ec-120">Kanal ile ilişkilendirilen uzak adres.</span><span class="sxs-lookup"><span data-stu-id="668ec-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="668ec-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="668ec-121">SessionId</span></span>  
 <span data-ttu-id="668ec-122">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="668ec-122">Data type: string</span></span>  
  
 <span data-ttu-id="668ec-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="668ec-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="668ec-124">Geçerli oturum kimliği, varsa.</span><span class="sxs-lookup"><span data-stu-id="668ec-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="668ec-125">Tür</span><span class="sxs-lookup"><span data-stu-id="668ec-125">Type</span></span>  
 <span data-ttu-id="668ec-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="668ec-126">Data type: string</span></span>  
  
 <span data-ttu-id="668ec-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="668ec-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="668ec-128">Kanal türü.</span><span class="sxs-lookup"><span data-stu-id="668ec-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="668ec-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="668ec-129">Requirements</span></span>  
  
|<span data-ttu-id="668ec-130">MOF</span><span class="sxs-lookup"><span data-stu-id="668ec-130">MOF</span></span>|<span data-ttu-id="668ec-131">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="668ec-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="668ec-132">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="668ec-132">Namespace</span></span>|<span data-ttu-id="668ec-133">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="668ec-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="668ec-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="668ec-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
