---
title: <add> ' ın <declaredTypes> öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: e6aab0b1eca340e212c34e2d25b9b84984dcc7a0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255516"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="47708-102">\<Ekle >, \<declaredTypes > öğesi</span><span class="sxs-lookup"><span data-stu-id="47708-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="47708-103">Tarafından kullanılan bir tür ekler <xref:System.Runtime.Serialization.DataContractSerializer> seri durumundan çıkarma sırasında.</span><span class="sxs-lookup"><span data-stu-id="47708-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="47708-104">Bildirilen her tür, alan veya özellik bildirilen tür döndürülecek bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="47708-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="47708-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="47708-105">system.runtime.serialization</span></span>  
<span data-ttu-id="47708-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="47708-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="47708-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="47708-107">\<declaredTypes></span></span>  
<span data-ttu-id="47708-108">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="47708-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47708-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47708-109">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47708-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="47708-110">Attributes and Elements</span></span>  
 <span data-ttu-id="47708-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="47708-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47708-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="47708-112">Attributes</span></span>  
  
|<span data-ttu-id="47708-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="47708-113">Attribute</span></span>|<span data-ttu-id="47708-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47708-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47708-115">türü</span><span class="sxs-lookup"><span data-stu-id="47708-115">type</span></span>|<span data-ttu-id="47708-116">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="47708-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="47708-117">Tür adı (ad uzayı dahil), derleme adı, sürüm numarasını, kültürü ve ortak anahtar belirteci belirtir.</span><span class="sxs-lookup"><span data-stu-id="47708-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47708-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="47708-118">Child Elements</span></span>  
  
|<span data-ttu-id="47708-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="47708-119">Element</span></span>|<span data-ttu-id="47708-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47708-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47708-121">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="47708-121">\<knownType></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|<span data-ttu-id="47708-122">Eklenmekte olan bildirilen türü bilinen türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="47708-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="47708-123">Bildirilen tür genel bir tür olduğu, ardından da bir parametre öğesine eklemeniz gerekir, `<knownType>` hangi genel parametre bilinen türü döndürmek için kullanıldığını belirtmek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="47708-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47708-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="47708-124">Parent Elements</span></span>  
  
|<span data-ttu-id="47708-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="47708-125">Element</span></span>|<span data-ttu-id="47708-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47708-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47708-127">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="47708-127">\<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<span data-ttu-id="47708-128">Tarafından seri durumundan çıkarma sırasında bilinen türler gerektiren türler içeren <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="47708-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47708-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47708-129">Remarks</span></span>  
 <span data-ttu-id="47708-130">Bilinen türler hakkında daha fazla bilgi için bkz: [veri sözleşme bilinen türleri](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="47708-130">For more information about known types, see [Data Contract Known Types](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="47708-131">Bkz: [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) bu öğe kullanma örneği için.</span><span class="sxs-lookup"><span data-stu-id="47708-131">See the [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="47708-132">Eklerseniz <xref:System.Object> olarak bir `<declaredType>`, <xref:System.Configuration.ConfigurationErrorsException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="47708-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="47708-133">Bunun nedeni, <xref:System.Object> türü yapılandırma bildirilen tür olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="47708-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47708-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="47708-134">Example</span></span>  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a><span data-ttu-id="47708-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="47708-135">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="47708-136">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="47708-136">Data Contract Known Types</span></span>](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="47708-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="47708-137">\<dataContractSerializer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [<span data-ttu-id="47708-138">\<Ekle >, \<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="47708-138">\<add> of \<declaredTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
