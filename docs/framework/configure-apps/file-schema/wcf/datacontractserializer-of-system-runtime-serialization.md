---
title: <dataContractSerializer><System. Runtime. Serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: eb556f533af1f99049382e9a2e34465f88d563db
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398087"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="ae5c2-102">\<dataContractSerializer> / \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="ae5c2-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="ae5c2-103">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="ae5c2-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="ae5c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae5c2-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae5c2-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae5c2-105">Attributes and Elements</span></span>  
 <span data-ttu-id="ae5c2-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ae5c2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae5c2-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ae5c2-107">Attributes</span></span>  
  
|<span data-ttu-id="ae5c2-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae5c2-108">Element</span></span>|<span data-ttu-id="ae5c2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae5c2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ae5c2-110">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="ae5c2-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="ae5c2-111">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="ae5c2-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="ae5c2-112">Bu öznitelik yalnızca `<dataContractSerializer>` öğesinin altında ayarlanabilir `<behavior>` .</span><span class="sxs-lookup"><span data-stu-id="ae5c2-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="ae5c2-113">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="ae5c2-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="ae5c2-114">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ae5c2-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="ae5c2-115">Bu öznitelik 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ae5c2-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae5c2-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae5c2-116">Child Elements</span></span>  
  
|<span data-ttu-id="ae5c2-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae5c2-117">Element</span></span>|<span data-ttu-id="ae5c2-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae5c2-118">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="ae5c2-119"><xref:System.Runtime.Serialization.DataContractSerializer>Seri durumdan çıkarılırken kullandığı bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ae5c2-119">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="ae5c2-120">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="ae5c2-120">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae5c2-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ae5c2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ae5c2-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="ae5c2-122">Element</span></span>|<span data-ttu-id="ae5c2-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae5c2-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="ae5c2-124">Ad alanı bölümünün kök öğesini temsil eder <xref:System.Runtime.Serialization> ve seçeneklerini ayarlamak için öğeleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="ae5c2-124">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae5c2-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae5c2-125">Remarks</span></span>  
 <span data-ttu-id="ae5c2-126">Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer> . ve [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="ae5c2-126">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae5c2-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae5c2-127">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="ae5c2-128">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="ae5c2-128">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
