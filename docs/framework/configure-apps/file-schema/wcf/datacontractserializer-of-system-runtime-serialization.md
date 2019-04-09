---
title: <dataContractSerializer> < system.runtime.serialization >
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: c81fdb040f2e0d6c9a3728d8ed3b917443ecb42e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115368"
---
# <a name="datacontractserializer-of-systemruntimeserialization"></a><span data-ttu-id="7cc14-102">\<dataContractSerializer >, \<system.runtime.serialization ></span><span class="sxs-lookup"><span data-stu-id="7cc14-102">\<dataContractSerializer> of \<system.runtime.serialization></span></span>
<span data-ttu-id="7cc14-103">İçin yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7cc14-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="7cc14-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="7cc14-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="7cc14-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="7cc14-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc14-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cc14-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cc14-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7cc14-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7cc14-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7cc14-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cc14-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7cc14-109">Attributes</span></span>  
  
|<span data-ttu-id="7cc14-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="7cc14-110">Element</span></span>|<span data-ttu-id="7cc14-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7cc14-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7cc14-112">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="7cc14-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="7cc14-113">Bunu edilirken bitiş noktası tarafından sağlanan veri yoksay belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="7cc14-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="7cc14-114">Bu öznitelik yalnızca ayarlanabilir `<dataContractSerializer>` altında `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="7cc14-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="7cc14-115">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="7cc14-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="7cc14-116">Serileştirmek veya seri durumdan çıkarılacak öğeleri maksimum sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="7cc14-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="7cc14-117">Bu öznitelik 65536'dır.</span><span class="sxs-lookup"><span data-stu-id="7cc14-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cc14-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7cc14-118">Child Elements</span></span>  
  
|<span data-ttu-id="7cc14-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="7cc14-119">Element</span></span>|<span data-ttu-id="7cc14-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7cc14-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cc14-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="7cc14-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="7cc14-122">İçerir, bilinen türleri <xref:System.Runtime.Serialization.DataContractSerializer> işlenirken kullanır.</span><span class="sxs-lookup"><span data-stu-id="7cc14-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="7cc14-123">Veri sözleşmeleri ve bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="7cc14-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7cc14-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7cc14-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7cc14-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="7cc14-125">Element</span></span>|<span data-ttu-id="7cc14-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7cc14-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cc14-127">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="7cc14-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="7cc14-128">İçin olan kök öğesini temsil eden <xref:System.Runtime.Serialization> ad uzayı bölümü ve seçeneklerini ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="7cc14-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cc14-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cc14-129">Remarks</span></span>  
 <span data-ttu-id="7cc14-130">Bilinen türler hakkında daha fazla bilgi için bkz: <xref:System.Runtime.Serialization.DataContractSerializer> ve [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="7cc14-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc14-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7cc14-131">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- [<span data-ttu-id="7cc14-132">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="7cc14-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
