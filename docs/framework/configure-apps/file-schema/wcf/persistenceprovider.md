---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 4fc9e1332effc51e183a84cf2d3653357277d2ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934147"
---
# <a name="persistenceprovider"></a><span data-ttu-id="8aa32-101">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="8aa32-101">\<persistenceProvider></span></span>
<span data-ttu-id="8aa32-102">Kullanılacak kalıcılık sağlayıcısı uygulamasının türünü ve Kalıcılık işlemleri için kullanılacak zaman aşımını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aa32-102">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
 <span data-ttu-id="8aa32-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8aa32-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="8aa32-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="8aa32-104">\<behaviors></span></span>  
<span data-ttu-id="8aa32-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8aa32-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="8aa32-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="8aa32-106">\<behavior></span></span>  
<span data-ttu-id="8aa32-107">\<persistenceProvider ></span><span class="sxs-lookup"><span data-stu-id="8aa32-107">\<persistenceProvider></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa32-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8aa32-108">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8aa32-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aa32-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8aa32-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8aa32-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8aa32-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8aa32-111">Attributes</span></span>  
  
|<span data-ttu-id="8aa32-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8aa32-112">Attribute</span></span>|<span data-ttu-id="8aa32-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aa32-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8aa32-114">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="8aa32-114">persistenceOperationTimeout</span></span>|<span data-ttu-id="8aa32-115">Kalıcılık <xref:System.TimeSpan> işlemleri için kullanılan zaman aşımını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="8aa32-115">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="8aa32-116">Varsayılan değer "00:00:30" dır.</span><span class="sxs-lookup"><span data-stu-id="8aa32-116">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="8aa32-117">türü</span><span class="sxs-lookup"><span data-stu-id="8aa32-117">type</span></span>|<span data-ttu-id="8aa32-118">Kullanılacak kalıcılık sağlayıcısı fabrikası türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="8aa32-118">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8aa32-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aa32-119">Child Elements</span></span>  
 <span data-ttu-id="8aa32-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="8aa32-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8aa32-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8aa32-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8aa32-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="8aa32-122">Element</span></span>|<span data-ttu-id="8aa32-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8aa32-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8aa32-124">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="8aa32-124">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8aa32-125">Bir davranış öğesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aa32-125">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8aa32-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8aa32-126">Remarks</span></span>  
 <span data-ttu-id="8aa32-127">Bu öğe, bir WCF hizmetinin durumunu seri hale getirmek için kullanılacak Kalıcılık sağlayıcısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="8aa32-127">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="8aa32-128">HTTP üst bilgilerinde durum bilgilerini geçiren ile `wsHttpContextBinding` birlikte kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8aa32-128">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa32-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8aa32-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
