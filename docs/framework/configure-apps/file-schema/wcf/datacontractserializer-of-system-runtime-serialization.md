---
title: <dataContractSerializer>< System. Runtime. Serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 380d9ba5b8407d78b5045fd34fcdf37c0818d6f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919345"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="32b79-102">\<\<System. Runtime. Serialization > için DataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="32b79-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="32b79-103">İçin yapılandırma verilerini içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="32b79-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="32b79-104">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="32b79-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="32b79-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="32b79-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32b79-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32b79-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32b79-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="32b79-107">Attributes and Elements</span></span>  
 <span data-ttu-id="32b79-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="32b79-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32b79-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="32b79-109">Attributes</span></span>  
  
|<span data-ttu-id="32b79-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="32b79-110">Element</span></span>|<span data-ttu-id="32b79-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32b79-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="32b79-112">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="32b79-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="32b79-113">Seri hale getirilmekte veya seri durumdan çıkarılmakta olduğu zaman, uç nokta tarafından sağlanan verilerin yoksayılıp yoksayılmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="32b79-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="32b79-114">Bu öznitelik yalnızca `<dataContractSerializer>` `<behavior>` öğesinin altında ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="32b79-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="32b79-115">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="32b79-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="32b79-116">Seri hale getirilecek veya seri durumdan çıkarılacak en fazla öğe sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="32b79-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="32b79-117">Bu öznitelik 65536 ' dir.</span><span class="sxs-lookup"><span data-stu-id="32b79-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32b79-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="32b79-118">Child Elements</span></span>  
  
|<span data-ttu-id="32b79-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="32b79-119">Element</span></span>|<span data-ttu-id="32b79-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32b79-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32b79-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="32b79-121">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="32b79-122">Seri durumdan çıkarılırken <xref:System.Runtime.Serialization.DataContractSerializer> kullandığı bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="32b79-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="32b79-123">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="32b79-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="32b79-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="32b79-124">Parent Elements</span></span>  
  
|<span data-ttu-id="32b79-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="32b79-125">Element</span></span>|<span data-ttu-id="32b79-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="32b79-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32b79-127">\<System. Runtime. Serialization ></span><span class="sxs-lookup"><span data-stu-id="32b79-127">\<system.runtime.serialization></span></span>](system-runtime-serialization.md)|<span data-ttu-id="32b79-128"><xref:System.Runtime.Serialization> Ad alanı bölümünün kök öğesini temsil eder ve seçeneklerini <xref:System.Runtime.Serialization.DataContractSerializer>ayarlamak için öğeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="32b79-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32b79-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32b79-129">Remarks</span></span>  
 <span data-ttu-id="32b79-130">Bilinen türler hakkında daha fazla bilgi için bkz <xref:System.Runtime.Serialization.DataContractSerializer> . ve [veri sözleşmesi bilinen türleri](../../../wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="32b79-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b79-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32b79-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="32b79-132">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="32b79-132">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
