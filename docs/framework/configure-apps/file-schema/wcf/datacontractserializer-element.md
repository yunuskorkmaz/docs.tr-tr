---
description: 'Hakkında daha fazla bilgi edinin: <dataContractSerializer>'
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 0705a40f55d76ef46a7debcd4ecfb5235c7c0d21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754439"
---
# \<dataContractSerializer>

<span data-ttu-id="6557b-102">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="6557b-102">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="6557b-103">Bu öğe iki farklı hiyerarşilerde oluşur.</span><span class="sxs-lookup"><span data-stu-id="6557b-103">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="6557b-104">Bunlardan biri aşağıdaki şema hiyerarşisi bölümünde listelenir ve diğer açıklamalar bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="6557b-104">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="6557b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6557b-105">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6557b-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6557b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="6557b-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6557b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6557b-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6557b-108">Attributes</span></span>  
  
|<span data-ttu-id="6557b-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="6557b-109">Element</span></span>|<span data-ttu-id="6557b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6557b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6557b-111">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="6557b-111">ignoreExtensionDataObject</span></span>|<span data-ttu-id="6557b-112">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="6557b-112">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="6557b-113">Bu öznitelik yalnızca `<dataContractSerializer>` öğesinin altında ayarlanabilir `<behavior>` .</span><span class="sxs-lookup"><span data-stu-id="6557b-113">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="6557b-114">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="6557b-114">maxItemsInObjectGraph</span></span>|<span data-ttu-id="6557b-115">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="6557b-115">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="6557b-116">Bu öznitelik 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="6557b-116">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6557b-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6557b-117">Child Elements</span></span>  

 <span data-ttu-id="6557b-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="6557b-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6557b-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6557b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="6557b-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="6557b-120">Element</span></span>|<span data-ttu-id="6557b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6557b-121">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="6557b-122">Bir hizmetin davranışına yönelik ayarların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="6557b-122">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="6557b-123">Ad alanı bölümünün kök öğesini temsil eder <xref:System.Runtime.Serialization> ve seçeneklerini ayarlamak için öğeleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="6557b-123">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6557b-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6557b-124">Remarks</span></span>  

 <span data-ttu-id="6557b-125">Bu konunun giriş bölümünde belirtildiği gibi, bu, öğesinin gerçekleştiği ikinci hiyerarşisidir \<X509Extension> .</span><span class="sxs-lookup"><span data-stu-id="6557b-125">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="6557b-126">Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer> ..</span><span class="sxs-lookup"><span data-stu-id="6557b-126">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6557b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6557b-127">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="6557b-128">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="6557b-128">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="6557b-129">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="6557b-129">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
