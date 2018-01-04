---
title: '&lt;dataContractSerializer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 27b80c831fdc66bd3b022645c3de9c0c31ee575a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltdatacontractserializergt"></a><span data-ttu-id="dc018-102">&lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="dc018-102">&lt;dataContractSerializer&gt;</span></span>
<span data-ttu-id="dc018-103">Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="dc018-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="dc018-104">Bu öğe, iki farklı hiyerarşilere oluşur.</span><span class="sxs-lookup"><span data-stu-id="dc018-104">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="dc018-105">Bir listelenir aşağıdaki şema hiyerarşisini bölümü ve diğer açıklamalar bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="dc018-105">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="dc018-106">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="dc018-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="dc018-107">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="dc018-107">\<behaviors></span></span>  
<span data-ttu-id="dc018-108">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="dc018-108">\<serviceBehaviors></span></span>  
<span data-ttu-id="dc018-109">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="dc018-109">\<behavior></span></span>  
<span data-ttu-id="dc018-110">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="dc018-110">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc018-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc018-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"  
   maxItemsInObjectGraph="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc018-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc018-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dc018-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc018-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc018-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dc018-114">Attributes</span></span>  
  
|<span data-ttu-id="dc018-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="dc018-115">Element</span></span>|<span data-ttu-id="dc018-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc018-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc018-117">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="dc018-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="dc018-118">Yüklenmekte olan zaman bitiş noktası tarafından sağlanan verileri yoksayacak şekilde belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="dc018-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="dc018-119">Bu öznitelik yalnızca ayarlanabilir `<dataContractSerializer>` altında `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="dc018-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="dc018-120">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="dc018-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="dc018-121">Tamsayı serileştirmek veya seri durumdan öğe sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc018-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="dc018-122">Bu öznitelik 65536'dır.</span><span class="sxs-lookup"><span data-stu-id="dc018-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc018-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc018-123">Child Elements</span></span>  
 <span data-ttu-id="dc018-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="dc018-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc018-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc018-125">Parent Elements</span></span>  
  
|<span data-ttu-id="dc018-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="dc018-126">Element</span></span>|<span data-ttu-id="dc018-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc018-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc018-128">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="dc018-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="dc018-129">Bir hizmet davranışını için ayarlar koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="dc018-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="dc018-130">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="dc018-130">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="dc018-131">Kök öğe için temsil eden <xref:System.Runtime.Serialization> ad alanı bölüm ve seçenekleri ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="dc018-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc018-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc018-132">Remarks</span></span>  
 <span data-ttu-id="dc018-133">Bu konuda girişte belirtildiği gibi bu ikinci hiyerarşisinde olan \<X509Extension > öğesi oluşur.</span><span class="sxs-lookup"><span data-stu-id="dc018-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="dc018-134">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="dc018-134">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="dc018-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="dc018-135">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="dc018-136">Bilinen türleri hakkında daha fazla bilgi için bkz: <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="dc018-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc018-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc018-137">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [<span data-ttu-id="dc018-138">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="dc018-138">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="dc018-139">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="dc018-139">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
