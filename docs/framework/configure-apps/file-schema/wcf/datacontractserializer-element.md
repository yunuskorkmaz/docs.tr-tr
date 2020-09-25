---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 2a994a8ba97d4c65fdaba5a85e779dd9935e3074
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195044"
---
# \<dataContractSerializer>

<span data-ttu-id="4fa2d-101">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="4fa2d-101">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="4fa2d-102">Bu öğe iki farklı hiyerarşilerde oluşur.</span><span class="sxs-lookup"><span data-stu-id="4fa2d-102">This element occurs in two different hierarchies.</span></span> <span data-ttu-id="4fa2d-103">Bunlardan biri aşağıdaki şema hiyerarşisi bölümünde listelenir ve diğer açıklamalar bölümünde listelenir.</span><span class="sxs-lookup"><span data-stu-id="4fa2d-103">One is listed the following Schema Hierarchy section and the other is listed in the Remarks section.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="4fa2d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="4fa2d-104">Syntax</span></span>  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fa2d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fa2d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="4fa2d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4fa2d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fa2d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4fa2d-107">Attributes</span></span>  
  
|<span data-ttu-id="4fa2d-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="4fa2d-108">Element</span></span>|<span data-ttu-id="4fa2d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fa2d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4fa2d-110">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="4fa2d-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="4fa2d-111">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="4fa2d-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="4fa2d-112">Bu öznitelik yalnızca `<dataContractSerializer>` öğesinin altında ayarlanabilir `<behavior>` .</span><span class="sxs-lookup"><span data-stu-id="4fa2d-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="4fa2d-113">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="4fa2d-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="4fa2d-114">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="4fa2d-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="4fa2d-115">Bu öznitelik 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="4fa2d-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fa2d-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fa2d-116">Child Elements</span></span>  

 <span data-ttu-id="4fa2d-117">Yok.</span><span class="sxs-lookup"><span data-stu-id="4fa2d-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fa2d-118">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4fa2d-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4fa2d-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="4fa2d-119">Element</span></span>|<span data-ttu-id="4fa2d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fa2d-120">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-servicebehaviors.md)|<span data-ttu-id="4fa2d-121">Bir hizmetin davranışına yönelik ayarların koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="4fa2d-121">A collection of settings for the behavior of a service.</span></span>|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="4fa2d-122">Ad alanı bölümünün kök öğesini temsil eder <xref:System.Runtime.Serialization> ve seçeneklerini ayarlamak için öğeleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="4fa2d-122">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fa2d-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4fa2d-123">Remarks</span></span>  

 <span data-ttu-id="4fa2d-124">Bu konunun giriş bölümünde belirtildiği gibi, bu, öğesinin gerçekleştiği ikinci hiyerarşisidir \<X509Extension> .</span><span class="sxs-lookup"><span data-stu-id="4fa2d-124">As stated in the Introduction of this topic, this is the second hierarchy in which the \<X509Extension> element occurs.</span></span>  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 <span data-ttu-id="4fa2d-125">Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer> ..</span><span class="sxs-lookup"><span data-stu-id="4fa2d-125">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa2d-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fa2d-126">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [<span data-ttu-id="4fa2d-127">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="4fa2d-127">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="4fa2d-128">Veri Aktarma ve Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="4fa2d-128">Data Transfer and Serialization</span></span>](../../../wcf/feature-details/data-transfer-and-serialization.md)
