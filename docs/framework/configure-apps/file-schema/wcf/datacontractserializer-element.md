---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 7e440810fee1dddb7025d1385b1edb4838d98a39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925919"
---
# <a name="datacontractserializer"></a><span data-ttu-id="6e8a9-101">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="6e8a9-101">\<dataContractSerializer></span></span>
<span data-ttu-id="6e8a9-102">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="6e8a9-103">Bu öğe iki farklı hiyerarşilerde oluşur.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="6e8a9-104">Bunlardan biri aşağıdaki şema hiyerarşisi bölümünde listelenir ve diğer açıklamalar bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
 <span data-ttu-id="6e8a9-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6e8a9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6e8a9-106">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="6e8a9-106">\<behaviors></span></span>  
<span data-ttu-id="6e8a9-107">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6e8a9-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="6e8a9-108">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="6e8a9-108">\<behavior></span></span>  
<span data-ttu-id="6e8a9-109">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="6e8a9-109">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e8a9-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e8a9-110">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e8a9-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e8a9-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6e8a9-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e8a9-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e8a9-113">Attributes</span></span>  
  
|<span data-ttu-id="6e8a9-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e8a9-114">Element</span></span>|<span data-ttu-id="6e8a9-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e8a9-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e8a9-116">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="6e8a9-116">ignoreExtensionDataObject</span></span>|<span data-ttu-id="6e8a9-117">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-117">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="6e8a9-118">Bu öznitelik yalnızca `<dataContractSerializer>` `<behavior>` öğesinin altında ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-118">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="6e8a9-119">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="6e8a9-119">maxItemsInObjectGraph</span></span>|<span data-ttu-id="6e8a9-120">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-120">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="6e8a9-121">Bu öznitelik 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-121">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6e8a9-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e8a9-122">Child Elements</span></span>  
 <span data-ttu-id="6e8a9-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6e8a9-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e8a9-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6e8a9-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e8a9-125">Element</span></span>|<span data-ttu-id="6e8a9-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e8a9-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e8a9-127">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="6e8a9-127">\<behavior></span></span>](behavior-of-servicebehaviors.md)|<span data-ttu-id="6e8a9-128">Bir hizmetin davranışına yönelik ayarların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-128">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="6e8a9-129">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="6e8a9-129">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="6e8a9-130"><xref:System.Runtime.Serialization> Ad alanı bölümünün kök öğesini temsil eder ve seçeneklerini <xref:System.Runtime.Serialization.DataContractSerializer>ayarlamak için öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-130">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e8a9-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e8a9-131">Remarks</span></span>  
 <span data-ttu-id="6e8a9-132">Bu konunun giriş bölümünde belirtildiği gibi, \<X509Extension > öğesinin gerçekleştiği ikinci hiyerarşisidir.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-132">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="6e8a9-133">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="6e8a9-133">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
  
 [<span data-ttu-id="6e8a9-134">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="6e8a9-134">\<dataContractSerializer></span></span>](datacontractserializer-element.md)  
  
 <span data-ttu-id="6e8a9-135">Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-135">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e8a9-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e8a9-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="6e8a9-137">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="6e8a9-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="6e8a9-138">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6e8a9-138">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
