---
title: '&lt;system.runtime.serialization&gt; &lt;dataContractSerializer&gt;'
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 3a959c9a4e2b1cbbbb6a52a1438261037704d244
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557974"
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a><span data-ttu-id="104a4-102">&lt;system.runtime.serialization&gt; &lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="104a4-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="104a4-103">İçin yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="104a4-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="104a4-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="104a4-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="104a4-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="104a4-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="104a4-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="104a4-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="104a4-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="104a4-107">Attributes and Elements</span></span>  
 <span data-ttu-id="104a4-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="104a4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="104a4-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="104a4-109">Attributes</span></span>  
  
|<span data-ttu-id="104a4-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="104a4-110">Element</span></span>|<span data-ttu-id="104a4-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="104a4-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="104a4-112">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="104a4-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="104a4-113">Bunu edilirken bitiş noktası tarafından sağlanan veri yoksay belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="104a4-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="104a4-114">Bu öznitelik yalnızca ayarlanabilir `<dataContractSerializer>` altında `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="104a4-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="104a4-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="104a4-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="104a4-116">Serileştirmek veya seri durumdan çıkarılacak öğeleri maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="104a4-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="104a4-117">Bu öznitelik 65536'dır.</span><span class="sxs-lookup"><span data-stu-id="104a4-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="104a4-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="104a4-118">Child Elements</span></span>  
  
|<span data-ttu-id="104a4-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="104a4-119">Element</span></span>|<span data-ttu-id="104a4-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="104a4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="104a4-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="104a4-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="104a4-122">İçerir, bilinen türleri <xref:System.Runtime.Serialization.DataContractSerializer> işlenirken kullanır.</span><span class="sxs-lookup"><span data-stu-id="104a4-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="104a4-123">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="104a4-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="104a4-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="104a4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="104a4-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="104a4-125">Element</span></span>|<span data-ttu-id="104a4-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="104a4-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="104a4-127">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="104a4-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="104a4-128">İçin olan kök öğesini temsil eden <xref:System.Runtime.Serialization> ad uzayı bölümü ve seçeneklerini ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="104a4-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="104a4-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="104a4-129">Remarks</span></span>  
 <span data-ttu-id="104a4-130">Bilinen türler hakkında daha fazla bilgi için bkz: <xref:System.Runtime.Serialization.DataContractSerializer> ve [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="104a4-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="104a4-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="104a4-131">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="104a4-132">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="104a4-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
