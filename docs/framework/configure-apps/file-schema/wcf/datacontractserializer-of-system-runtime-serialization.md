---
description: <dataContractSerializer><System. Runtime. serialization> hakkında daha fazla bilgi edinin
title: <dataContractSerializer> <System. Runtime. Serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 3755005782ea773344326d211b9f8f115a97f2ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754426"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="cd1e5-103">\<dataContractSerializer> / \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="cd1e5-103">\<dataContractSerializer> of \<system.runtime.serialization></span></span>

<span data-ttu-id="cd1e5-104">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="cd1e5-104">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="cd1e5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cd1e5-105">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer"
                       type="String" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd1e5-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd1e5-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cd1e5-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cd1e5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd1e5-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cd1e5-108">Attributes</span></span>  
  
|<span data-ttu-id="cd1e5-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd1e5-109">Element</span></span>|<span data-ttu-id="cd1e5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd1e5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd1e5-111">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="cd1e5-111">ignoreExtensionDataObject</span></span>|<span data-ttu-id="cd1e5-112">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="cd1e5-112">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="cd1e5-113">Bu öznitelik yalnızca `<dataContractSerializer>` öğesinin altında ayarlanabilir `<behavior>` .</span><span class="sxs-lookup"><span data-stu-id="cd1e5-113">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="cd1e5-114">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="cd1e5-114">maxItemsInObjectGraph</span></span>|<span data-ttu-id="cd1e5-115">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="cd1e5-115">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="cd1e5-116">Bu öznitelik 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="cd1e5-116">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd1e5-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd1e5-117">Child Elements</span></span>  
  
|<span data-ttu-id="cd1e5-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd1e5-118">Element</span></span>|<span data-ttu-id="cd1e5-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd1e5-119">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="cd1e5-120"><xref:System.Runtime.Serialization.DataContractSerializer>Seri durumdan çıkarılırken kullandığı bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cd1e5-120">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="cd1e5-121">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="cd1e5-121">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd1e5-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cd1e5-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cd1e5-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="cd1e5-123">Element</span></span>|<span data-ttu-id="cd1e5-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cd1e5-124">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="cd1e5-125">Ad alanı bölümünün kök öğesini temsil eder <xref:System.Runtime.Serialization> ve seçeneklerini ayarlamak için öğeleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="cd1e5-125">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd1e5-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cd1e5-126">Remarks</span></span>  

 <span data-ttu-id="cd1e5-127">Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer> . ve [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="cd1e5-127">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd1e5-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd1e5-128">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="cd1e5-129">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="cd1e5-129">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
