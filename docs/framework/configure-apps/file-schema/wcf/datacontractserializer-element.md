---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: b635f03d1e4a6628a76d678f7366482717276376
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704147"
---
# <a name="datacontractserializer"></a><span data-ttu-id="c6916-101">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c6916-101">\<dataContractSerializer></span></span>
<span data-ttu-id="c6916-102">İçin yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c6916-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="c6916-103">Bu öğe, iki farklı hiyerarşilere gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="c6916-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="c6916-104">Bir listelenir aşağıdaki şema hiyerarşisini bölümü ve diğer açıklamalar bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="c6916-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="c6916-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c6916-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c6916-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="c6916-106">\<behaviors></span></span>  
<span data-ttu-id="c6916-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="c6916-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="c6916-108">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="c6916-108">\<behavior></span></span>  
<span data-ttu-id="c6916-109">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c6916-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6916-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c6916-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6916-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6916-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c6916-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c6916-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6916-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c6916-113">Attributes</span></span>  
  
|<span data-ttu-id="c6916-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6916-114">Element</span></span>|<span data-ttu-id="c6916-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6916-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6916-116">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="c6916-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="c6916-117">Bunu edilirken bitiş noktası tarafından sağlanan veri yoksay belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="c6916-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="c6916-118">Bu öznitelik yalnızca ayarlanabilir `<dataContractSerializer>` altında `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="c6916-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="c6916-119">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="c6916-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="c6916-120">Serileştirmek veya seri durumdan çıkarılacak öğeleri maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c6916-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="c6916-121">Bu öznitelik 65536'dır.</span><span class="sxs-lookup"><span data-stu-id="c6916-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6916-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6916-122">Child Elements</span></span>  
 <span data-ttu-id="c6916-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="c6916-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6916-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c6916-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c6916-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="c6916-125">Element</span></span>|<span data-ttu-id="c6916-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6916-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6916-127">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="c6916-127">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|<span data-ttu-id="c6916-128">Bir koleksiyon için bir hizmet davranışını ayarlar.</span><span class="sxs-lookup"><span data-stu-id="c6916-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="c6916-129">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="c6916-129">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="c6916-130">İçin olan kök öğesini temsil eden <xref:System.Runtime.Serialization> ad uzayı bölümü ve seçeneklerini ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c6916-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6916-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c6916-131">Remarks</span></span>  
 <span data-ttu-id="c6916-132">Bu konunun giriş belirtildiği gibi ikinci hiyerarşide budur \<X509Extension > öğesi oluşur.</span><span class="sxs-lookup"><span data-stu-id="c6916-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="c6916-133">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="c6916-133">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [<span data-ttu-id="c6916-134">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c6916-134">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 <span data-ttu-id="c6916-135">Bilinen türler hakkında daha fazla bilgi için bkz: <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c6916-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6916-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6916-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="c6916-137">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="c6916-137">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="c6916-138">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c6916-138">Data Transfer and Serialization</span></span>](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
