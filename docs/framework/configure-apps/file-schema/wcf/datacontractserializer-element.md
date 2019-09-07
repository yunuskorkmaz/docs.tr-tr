---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: e24dae47171f741af064ca2eaa822928690acf6e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400445"
---
# <a name="datacontractserializer"></a><span data-ttu-id="c86dc-101">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c86dc-101">\<dataContractSerializer></span></span>
<span data-ttu-id="c86dc-102">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c86dc-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="c86dc-103">Bu öğe iki farklı hiyerarşilerde oluşur.</span><span class="sxs-lookup"><span data-stu-id="c86dc-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="c86dc-104">Bunlardan biri aşağıdaki şema hiyerarşisi bölümünde listelenir ve diğer açıklamalar bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="c86dc-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
<span data-ttu-id="c86dc-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c86dc-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c86dc-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c86dc-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c86dc-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c86dc-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c86dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c86dc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="c86dc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c86dc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="c86dc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dataContractSerializer >**</span><span class="sxs-lookup"><span data-stu-id="c86dc-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c86dc-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c86dc-111">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c86dc-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c86dc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c86dc-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c86dc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c86dc-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c86dc-114">Attributes</span></span>  
  
|<span data-ttu-id="c86dc-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="c86dc-115">Element</span></span>|<span data-ttu-id="c86dc-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c86dc-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c86dc-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="c86dc-117">ignoreExtensionDataObject</span></span>|<span data-ttu-id="c86dc-118">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="c86dc-118">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="c86dc-119">Bu öznitelik yalnızca `<dataContractSerializer>` `<behavior>` öğesinin altında ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c86dc-119">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="c86dc-120">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="c86dc-120">maxItemsInObjectGraph</span></span>|<span data-ttu-id="c86dc-121">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="c86dc-121">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="c86dc-122">Bu öznitelik 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="c86dc-122">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c86dc-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c86dc-123">Child Elements</span></span>  
 <span data-ttu-id="c86dc-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="c86dc-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c86dc-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c86dc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c86dc-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="c86dc-126">Element</span></span>|<span data-ttu-id="c86dc-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c86dc-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c86dc-128">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="c86dc-128">\<behavior></span></span>](behavior-of-servicebehaviors.md)|<span data-ttu-id="c86dc-129">Bir hizmetin davranışına yönelik ayarların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="c86dc-129">A collection of settings for the behavior of a service.</span></span>|  
|[<span data-ttu-id="c86dc-130">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="c86dc-130">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="c86dc-131"><xref:System.Runtime.Serialization> Ad alanı bölümünün kök öğesini temsil eder ve seçeneklerini <xref:System.Runtime.Serialization.DataContractSerializer>ayarlamak için öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c86dc-131">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c86dc-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c86dc-132">Remarks</span></span>  
 <span data-ttu-id="c86dc-133">Bu konunun giriş bölümünde belirtildiği gibi, \<X509Extension > öğesinin gerçekleştiği ikinci hiyerarşisidir.</span><span class="sxs-lookup"><span data-stu-id="c86dc-133">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [<span data-ttu-id="c86dc-134">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="c86dc-134">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)  
  
 [<span data-ttu-id="c86dc-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="c86dc-135">\<dataContractSerializer></span></span>](datacontractserializer-element.md)  
  
 <span data-ttu-id="c86dc-136">Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c86dc-136">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c86dc-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c86dc-137">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="c86dc-138">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="c86dc-138">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="c86dc-139">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="c86dc-139">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
