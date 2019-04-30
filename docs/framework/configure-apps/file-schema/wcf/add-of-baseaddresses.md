---
title: <add> / <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: fbcb3a07bf40c96a4cd1b2ec87277b6fefdfb89d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704459"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="e7ac0-102">\<Ekle >, \<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="e7ac0-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="e7ac0-103">Hizmet ana bilgisayarı tarafından kullanılan tabanı belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="e7ac0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e7ac0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e7ac0-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="e7ac0-105">\<client></span></span>  
<span data-ttu-id="e7ac0-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="e7ac0-106">\<endpoint></span></span>  
<span data-ttu-id="e7ac0-107">\<konak ></span><span class="sxs-lookup"><span data-stu-id="e7ac0-107">\<host></span></span>  
<span data-ttu-id="e7ac0-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="e7ac0-108">\<baseAddresses></span></span>  
<span data-ttu-id="e7ac0-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="e7ac0-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7ac0-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7ac0-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="e7ac0-111">Tür</span><span class="sxs-lookup"><span data-stu-id="e7ac0-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7ac0-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7ac0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e7ac0-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7ac0-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e7ac0-114">Attributes</span></span>  
  
|<span data-ttu-id="e7ac0-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e7ac0-115">Attribute</span></span>|<span data-ttu-id="e7ac0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7ac0-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="e7ac0-117">Hizmet ana bilgisayarı tarafından kullanılan taban adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7ac0-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7ac0-118">Child Elements</span></span>  
 <span data-ttu-id="e7ac0-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7ac0-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7ac0-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e7ac0-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="e7ac0-121">Element</span></span>|<span data-ttu-id="e7ac0-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7ac0-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7ac0-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="e7ac0-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="e7ac0-124">Bir koleksiyonu `baseAddress` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7ac0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7ac0-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="e7ac0-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e7ac0-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
