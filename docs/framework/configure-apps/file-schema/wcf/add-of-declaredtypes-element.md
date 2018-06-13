---
title: '&lt;declaredTypes&gt; Öğesi &lt;ekleme&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 90eaf11ce8b9e3675a23ed3875680b03f149b56b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754125"
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a><span data-ttu-id="11f60-102">&lt;declaredTypes&gt; Öğesi &lt;ekleme&gt;</span><span class="sxs-lookup"><span data-stu-id="11f60-102">&lt;add&gt; of &lt;declaredTypes&gt; Element</span></span>
<span data-ttu-id="11f60-103">Tarafından kullanılan bir tür ekler <xref:System.Runtime.Serialization.DataContractSerializer> seri durumdan çıkarma sırasında.</span><span class="sxs-lookup"><span data-stu-id="11f60-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="11f60-104">Bildirilen her türü, bir alan veya özellik bildirilen türü döndürülecek bilinen türler içerir.</span><span class="sxs-lookup"><span data-stu-id="11f60-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="11f60-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="11f60-105">system.runtime.serialization</span></span>  
<span data-ttu-id="11f60-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="11f60-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="11f60-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="11f60-107">\<declaredTypes></span></span>  
<span data-ttu-id="11f60-108">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="11f60-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11f60-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="11f60-109">Syntax</span></span>  
  
```xml  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11f60-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="11f60-110">Attributes and Elements</span></span>  
 <span data-ttu-id="11f60-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="11f60-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11f60-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="11f60-112">Attributes</span></span>  
  
|<span data-ttu-id="11f60-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="11f60-113">Attribute</span></span>|<span data-ttu-id="11f60-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11f60-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11f60-115">türü</span><span class="sxs-lookup"><span data-stu-id="11f60-115">type</span></span>|<span data-ttu-id="11f60-116">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="11f60-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="11f60-117">Tür adı (ad alanı dahil), derleme adı, sürüm numarası, kültür ve ortak anahtar belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="11f60-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11f60-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="11f60-118">Child Elements</span></span>  
  
|<span data-ttu-id="11f60-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="11f60-119">Element</span></span>|<span data-ttu-id="11f60-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11f60-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11f60-121">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="11f60-121">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="11f60-122">Eklenmekte olan türü için bilinen türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="11f60-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="11f60-123">Genel bir tür bildirilen türüdür sonra da bir parametre öğesine eklemelisiniz `<knownType>` öğesi bilinen türü döndürmek için kullanılan hangi genel parametresini belirtin.</span><span class="sxs-lookup"><span data-stu-id="11f60-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11f60-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="11f60-124">Parent Elements</span></span>  
  
|<span data-ttu-id="11f60-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="11f60-125">Element</span></span>|<span data-ttu-id="11f60-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="11f60-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11f60-127">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="11f60-127">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="11f60-128">Bilinen türler tarafından seri durumdan çıkarma sırasında gerektiren türleri içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="11f60-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11f60-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11f60-129">Remarks</span></span>  
 <span data-ttu-id="11f60-130">Bilinen türleri hakkında daha fazla bilgi için bkz: [veri sözleşmesi bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="11f60-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="11f60-131">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="11f60-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11f60-132">Eklerseniz <xref:System.Object> olarak yazın bir `<declaredType>`, <xref:System.Configuration.ConfigurationErrorsException> atılır.</span><span class="sxs-lookup"><span data-stu-id="11f60-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="11f60-133">Bunun nedeni, <xref:System.Object> türü, yapılandırmada bildirilen türü olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="11f60-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11f60-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="11f60-134">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11f60-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="11f60-135">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="11f60-136">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="11f60-136">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [<span data-ttu-id="11f60-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="11f60-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [<span data-ttu-id="11f60-138">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="11f60-138">\<add> of \<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
