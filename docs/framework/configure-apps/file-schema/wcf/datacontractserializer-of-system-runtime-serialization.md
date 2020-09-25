---
title: <dataContractSerializer> <System. Runtime. Serialization>
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: a8d379e7a37bca0cdb58836a6afdf814320e2411
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190195"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="15e3d-102">\<dataContractSerializer> / \<system.runtime.serialization></span><span class="sxs-lookup"><span data-stu-id="15e3d-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>

<span data-ttu-id="15e3d-103">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="15e3d-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<dataContractSerializer>**  
  
## <a name="syntax"></a><span data-ttu-id="15e3d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="15e3d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15e3d-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="15e3d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="15e3d-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="15e3d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15e3d-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="15e3d-107">Attributes</span></span>  
  
|<span data-ttu-id="15e3d-108">Öğe</span><span class="sxs-lookup"><span data-stu-id="15e3d-108">Element</span></span>|<span data-ttu-id="15e3d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15e3d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15e3d-110">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="15e3d-110">ignoreExtensionDataObject</span></span>|<span data-ttu-id="15e3d-111">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="15e3d-111">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="15e3d-112">Bu öznitelik yalnızca `<dataContractSerializer>` öğesinin altında ayarlanabilir `<behavior>` .</span><span class="sxs-lookup"><span data-stu-id="15e3d-112">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="15e3d-113">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="15e3d-113">maxItemsInObjectGraph</span></span>|<span data-ttu-id="15e3d-114">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="15e3d-114">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="15e3d-115">Bu öznitelik 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="15e3d-115">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15e3d-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="15e3d-116">Child Elements</span></span>  
  
|<span data-ttu-id="15e3d-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="15e3d-117">Element</span></span>|<span data-ttu-id="15e3d-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15e3d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="15e3d-119"><xref:System.Runtime.Serialization.DataContractSerializer>Seri durumdan çıkarılırken kullandığı bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="15e3d-119">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="15e3d-120">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="15e3d-120">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15e3d-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="15e3d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="15e3d-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="15e3d-122">Element</span></span>|<span data-ttu-id="15e3d-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="15e3d-123">Description</span></span>|  
|-------------|-----------------|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|<span data-ttu-id="15e3d-124">Ad alanı bölümünün kök öğesini temsil eder <xref:System.Runtime.Serialization> ve seçeneklerini ayarlamak için öğeleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="15e3d-124">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15e3d-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="15e3d-125">Remarks</span></span>  

 <span data-ttu-id="15e3d-126">Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer> . ve [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="15e3d-126">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e3d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15e3d-127">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="15e3d-128">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="15e3d-128">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
