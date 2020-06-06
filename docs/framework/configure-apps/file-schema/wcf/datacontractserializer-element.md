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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400445"
---
# \<dataContractSerializer>
<span data-ttu-id="bcb59-101">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="bcb59-101">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="bcb59-102">Bu öğe iki farklı hiyerarşilerde oluşur.</span><span class="sxs-lookup"><span data-stu-id="bcb59-102">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="bcb59-103">Bunlardan biri aşağıdaki şema hiyerarşisi bölümünde listelenir ve diğer açıklamalar bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="bcb59-103">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="bcb59-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bcb59-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bcb59-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bcb59-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bcb59-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bcb59-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bcb59-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bcb59-107">Attributes</span></span>  
  
|<span data-ttu-id="bcb59-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="bcb59-108">Element</span></span>|<span data-ttu-id="bcb59-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bcb59-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bcb59-110">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="bcb59-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="bcb59-111">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="bcb59-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="bcb59-112">Bu öznitelik yalnızca `<dataContractSerializer>` öğesinin altında ayarlanabilir `<behavior>` .</span><span class="sxs-lookup"><span data-stu-id="bcb59-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="bcb59-113">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="bcb59-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="bcb59-114">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="bcb59-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="bcb59-115">Bu öznitelik 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="bcb59-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bcb59-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bcb59-116">Child Elements</span></span>  
 <span data-ttu-id="bcb59-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="bcb59-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bcb59-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bcb59-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bcb59-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="bcb59-119">Element</span></span>|<span data-ttu-id="bcb59-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bcb59-120">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="bcb59-121">Bir hizmetin davranışına yönelik ayarların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bcb59-121">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="bcb59-122">Ad alanı bölümünün kök öğesini temsil eder <xref:System.Runtime.Serialization> ve seçeneklerini ayarlamak için öğeleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="bcb59-122">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcb59-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bcb59-123">Remarks</span></span>  
 <span data-ttu-id="bcb59-124">Bu konunun giriş bölümünde belirtildiği gibi, bu, öğesinin gerçekleştiği ikinci hiyerarşisidir \<X509Extension> .</span><span class="sxs-lookup"><span data-stu-id="bcb59-124">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="bcb59-125">Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer> ..</span><span class="sxs-lookup"><span data-stu-id="bcb59-125">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb59-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcb59-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="bcb59-127">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="bcb59-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="bcb59-128">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="bcb59-128">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
