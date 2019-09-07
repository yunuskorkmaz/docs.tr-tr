---
title: <dataContractSerializer>< System. Runtime. Serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: eb556f533af1f99049382e9a2e34465f88d563db
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398087"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="313d7-102">\<\<System. Runtime. Serialization > için DataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="313d7-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="313d7-103">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="313d7-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
<span data-ttu-id="313d7-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="313d7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="313d7-105">&nbsp;&nbsp;[ **\<System. Runtime. Serialization >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="313d7-105">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="313d7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<dataContractSerializer >**</span><span class="sxs-lookup"><span data-stu-id="313d7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="313d7-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="313d7-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="313d7-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="313d7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="313d7-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="313d7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="313d7-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="313d7-110">Attributes</span></span>  
  
|<span data-ttu-id="313d7-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="313d7-111">Element</span></span>|<span data-ttu-id="313d7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="313d7-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="313d7-113">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="313d7-113">ignoreExtensionDataObject</span></span>|<span data-ttu-id="313d7-114">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="313d7-114">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="313d7-115">Bu öznitelik yalnızca `<dataContractSerializer>` `<behavior>` öğesinin altında ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="313d7-115">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="313d7-116">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="313d7-116">maxItemsInObjectGraph</span></span>|<span data-ttu-id="313d7-117">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="313d7-117">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="313d7-118">Bu öznitelik 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="313d7-118">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="313d7-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="313d7-119">Child Elements</span></span>  
  
|<span data-ttu-id="313d7-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="313d7-120">Element</span></span>|<span data-ttu-id="313d7-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="313d7-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="313d7-122">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="313d7-122">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="313d7-123">Seri durumdan çıkarılırken <xref:System.Runtime.Serialization.DataContractSerializer> kullandığı bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="313d7-123">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="313d7-124">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="313d7-124">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="313d7-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="313d7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="313d7-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="313d7-126">Element</span></span>|<span data-ttu-id="313d7-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="313d7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="313d7-128">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="313d7-128">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="313d7-129"><xref:System.Runtime.Serialization> Ad alanı bölümünün kök öğesini temsil eder ve seçeneklerini <xref:System.Runtime.Serialization.DataContractSerializer>ayarlamak için öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="313d7-129">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="313d7-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="313d7-130">Remarks</span></span>  
 <span data-ttu-id="313d7-131">Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer> . ve [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="313d7-131">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="313d7-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="313d7-132">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="313d7-133">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="313d7-133">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
