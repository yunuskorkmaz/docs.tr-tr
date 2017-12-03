---
title: '&lt;persistenceProvider&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2d93a9ea8614f98c968d499c2f95dcd3962f0020
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltpersistenceprovidergt"></a><span data-ttu-id="73114-102">&lt;persistenceProvider&gt;</span><span class="sxs-lookup"><span data-stu-id="73114-102">&lt;persistenceProvider&gt;</span></span>
<span data-ttu-id="73114-103">Kalıcılık işlemleri için zaman aşımı yanı sıra kullanmak için Kalıcılık sağlayıcı uygulaması türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="73114-103">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="73114-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="73114-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="73114-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="73114-105">\<behaviors></span></span>  
<span data-ttu-id="73114-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="73114-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="73114-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="73114-107">\<behavior></span></span>  
<span data-ttu-id="73114-108">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="73114-108">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73114-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="73114-109">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"  
   type="String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73114-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="73114-110">Attributes and Elements</span></span>  
 <span data-ttu-id="73114-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73114-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73114-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="73114-112">Attributes</span></span>  
  
|<span data-ttu-id="73114-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="73114-113">Attribute</span></span>|<span data-ttu-id="73114-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73114-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73114-115">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="73114-115">persistenceOperationTimeout</span></span>|<span data-ttu-id="73114-116">A <xref:System.TimeSpan> Kalıcılık işlemleri için kullanılan zaman aşımı belirten değer.</span><span class="sxs-lookup"><span data-stu-id="73114-116">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="73114-117">Varsayılan değer "00: 00:30".</span><span class="sxs-lookup"><span data-stu-id="73114-117">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="73114-118">türü</span><span class="sxs-lookup"><span data-stu-id="73114-118">type</span></span>|<span data-ttu-id="73114-119">Kullanılacak Kalıcılık sağlayıcı üreteci türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="73114-119">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73114-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="73114-120">Child Elements</span></span>  
 <span data-ttu-id="73114-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="73114-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73114-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="73114-122">Parent Elements</span></span>  
  
|<span data-ttu-id="73114-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="73114-123">Element</span></span>|<span data-ttu-id="73114-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="73114-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73114-125">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="73114-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="73114-126">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="73114-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73114-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="73114-127">Remarks</span></span>  
 <span data-ttu-id="73114-128">Bu öğe bir WCF Hizmeti durumunu serileştirmek için kullanılacak Kalıcılık sağlayıcıyı belirtir.</span><span class="sxs-lookup"><span data-stu-id="73114-128">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="73114-129">İle birlikte kullanılmalıdır `wsHttpContextBinding` HTTP üstbilgilerinde durum bilgilerini geçirir.</span><span class="sxs-lookup"><span data-stu-id="73114-129">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73114-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="73114-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PersistenceProviderElement>  
 <xref:System.ServiceModel.Persistence.PersistenceProvider>
