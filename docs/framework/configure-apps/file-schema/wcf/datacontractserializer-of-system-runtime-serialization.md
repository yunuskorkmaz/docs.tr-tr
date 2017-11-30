---
title: '&lt;system.runtime.serialization&gt; &lt;dataContractSerializer&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9b3d625-be3f-4768-8e0d-1b7e6929f6a8
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e0c8d0e82696935a480935ebbb71530e052f8d8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltdatacontractserializergt-of-ltsystemruntimeserializationgt"></a><span data-ttu-id="16a1e-102">&lt;system.runtime.serialization&gt; &lt;dataContractSerializer&gt;</span><span class="sxs-lookup"><span data-stu-id="16a1e-102">&lt;dataContractSerializer&gt; of &lt;system.runtime.serialization&gt;</span></span>
<span data-ttu-id="16a1e-103">Yapılandırma verilerini içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="16a1e-103">Contains configuration data for the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="16a1e-104">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="16a1e-104">\<system.runtime.serialization></span></span>  
<span data-ttu-id="16a1e-105">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="16a1e-105">\<dataContractSerializer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16a1e-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16a1e-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16a1e-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="16a1e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="16a1e-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="16a1e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16a1e-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="16a1e-109">Attributes</span></span>  
  
|<span data-ttu-id="16a1e-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="16a1e-110">Element</span></span>|<span data-ttu-id="16a1e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16a1e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="16a1e-112">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="16a1e-112">ignoreExtensionDataObject</span></span>|<span data-ttu-id="16a1e-113">Yüklenmekte olan zaman bitiş noktası tarafından sağlanan verileri yoksayacak şekilde belirten bir Boole değeri serileştirilecek veya serisi.</span><span class="sxs-lookup"><span data-stu-id="16a1e-113">A Boolean value that specifies whether to ignore data supplied by the endpoint when it is being serialized or deserialized.</span></span> <span data-ttu-id="16a1e-114">Bu öznitelik yalnızca ayarlanabilir `<dataContractSerializer>` altında `<behavior>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="16a1e-114">This attribute is settable only on the `<dataContractSerializer>` under the `<behavior>` element.</span></span>|  
|<span data-ttu-id="16a1e-115">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="16a1e-115">maxItemsInObjectGraph</span></span>|<span data-ttu-id="16a1e-116">Tamsayı serileştirmek veya seri durumdan öğe sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="16a1e-116">An integer that specifies the maximum number of items to serialize or deserialize.</span></span> <span data-ttu-id="16a1e-117">Bu öznitelik 65536'dır.</span><span class="sxs-lookup"><span data-stu-id="16a1e-117">This attribute is 65536.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16a1e-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="16a1e-118">Child Elements</span></span>  
  
|<span data-ttu-id="16a1e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="16a1e-119">Element</span></span>|<span data-ttu-id="16a1e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16a1e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16a1e-121">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="16a1e-121">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="16a1e-122">İçeren bilinen türleri <xref:System.Runtime.Serialization.DataContractSerializer> çıkarılırken kullanır.</span><span class="sxs-lookup"><span data-stu-id="16a1e-122">Contains the known types that the <xref:System.Runtime.Serialization.DataContractSerializer> uses when deserializing.</span></span><br /><br /> <span data-ttu-id="16a1e-123">Veri sözleşmeleri ve bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="16a1e-123">For more information about data contracts and known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16a1e-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="16a1e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="16a1e-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="16a1e-125">Element</span></span>|<span data-ttu-id="16a1e-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="16a1e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16a1e-127">\<System.Runtime.Serialization ></span><span class="sxs-lookup"><span data-stu-id="16a1e-127">\<system.runtime.serialization></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|<span data-ttu-id="16a1e-128">Kök öğe için temsil eden <xref:System.Runtime.Serialization> ad alanı bölüm ve seçenekleri ayarlamak için öğeleri içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="16a1e-128">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16a1e-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16a1e-129">Remarks</span></span>  
 <span data-ttu-id="16a1e-130">Bilinen türleri hakkında daha fazla bilgi için bkz: <xref:System.Runtime.Serialization.DataContractSerializer> ve [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="16a1e-130">For more information about known types, see <xref:System.Runtime.Serialization.DataContractSerializer> and [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16a1e-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16a1e-131">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 [<span data-ttu-id="16a1e-132">Veri sözleşmesi bilinen türler</span><span class="sxs-lookup"><span data-stu-id="16a1e-132">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
