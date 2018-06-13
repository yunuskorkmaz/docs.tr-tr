---
title: '&lt;system.runtime.serialization&gt; &lt;dataContractSerializer&gt;'
ms.date: 03/30/2017
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
ms.openlocfilehash: 96802100fe1b91d3e375363d2c36e239b1a1d330
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747713"
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a><span data-ttu-id="fb4ca-102">&lt;system.runtime.serialization&gt; &lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="fb4ca-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="fb4ca-103">Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fb4ca-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="fb4ca-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="fb4ca-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="fb4ca-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="fb4ca-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb4ca-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb4ca-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb4ca-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb4ca-107">Attributes and Elements</span></span>  
 <span data-ttu-id="fb4ca-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fb4ca-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb4ca-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="fb4ca-109">Attributes</span></span>  
  
|<span data-ttu-id="fb4ca-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb4ca-110">Element</span></span>|<span data-ttu-id="fb4ca-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb4ca-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fb4ca-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="fb4ca-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="fb4ca-113">Yüklenmekte olan zaman bitiş noktası tarafından sağlanan verileri yoksayacak şekilde belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="fb4ca-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="fb4ca-114">Bu öznitelik yalnızca ayarlanabilir `<dataContractSerializer>` altında `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="fb4ca-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="fb4ca-115">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="fb4ca-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="fb4ca-116">Tamsayı serileştirmek veya seri durumdan öğe sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="fb4ca-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="fb4ca-117">Bu öznitelik 65536'dır.</span><span class="sxs-lookup"><span data-stu-id="fb4ca-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb4ca-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb4ca-118">Child Elements</span></span>  
  
|<span data-ttu-id="fb4ca-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb4ca-119">Element</span></span>|<span data-ttu-id="fb4ca-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb4ca-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb4ca-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="fb4ca-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="fb4ca-122">İçeren bilinen türleri <xref:System.Runtime.Serialization.DataContractSerializer> çıkarılırken kullanır.</span><span class="sxs-lookup"><span data-stu-id="fb4ca-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="fb4ca-123">Veri sözleşmeleri ve bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="fb4ca-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fb4ca-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="fb4ca-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fb4ca-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="fb4ca-125">Element</span></span>|<span data-ttu-id="fb4ca-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb4ca-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb4ca-127">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="fb4ca-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="fb4ca-128">Kök öğe için temsil eden <xref:System.Runtime.Serialization> ad alanı bölüm ve seçenekleri ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fb4ca-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb4ca-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb4ca-129">Remarks</span></span>  
 <span data-ttu-id="fb4ca-130">Bilinen türleri hakkında daha fazla bilgi için bkz: <xref:System.Runtime.Serialization.DataContractSerializer> ve [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="fb4ca-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb4ca-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fb4ca-131">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 [<span data-ttu-id="fb4ca-132">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="fb4ca-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
