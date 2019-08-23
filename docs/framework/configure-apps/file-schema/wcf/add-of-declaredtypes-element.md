---
title: <add><declaredTypes> öğesinin
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 1ea008dcc72d555b00e9648ace95bb9522ffc2c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920182"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="4de5e-102">\<\<DeclaredTypes > öğesinin > ekleyin</span><span class="sxs-lookup"><span data-stu-id="4de5e-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="4de5e-103">Seri durumdan çıkarma <xref:System.Runtime.Serialization.DataContractSerializer> sırasında tarafından kullanılan bir tür ekler.</span><span class="sxs-lookup"><span data-stu-id="4de5e-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="4de5e-104">Her bir tanımlı tür, bir alan veya tanımlanmış türün özelliği olarak döndürülecek bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4de5e-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
 <span data-ttu-id="4de5e-105">system.runtime.serialization</span><span class="sxs-lookup"><span data-stu-id="4de5e-105">system.runtime.serialization</span></span>  
<span data-ttu-id="4de5e-106">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="4de5e-106">\<dataContractSerializer></span></span>  
<span data-ttu-id="4de5e-107">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="4de5e-107">\<declaredTypes></span></span>  
<span data-ttu-id="4de5e-108">\<\<DeclaredTypes > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="4de5e-108">\<add> of \<declaredTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4de5e-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4de5e-109">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4de5e-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4de5e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4de5e-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4de5e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4de5e-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4de5e-112">Attributes</span></span>  
  
|<span data-ttu-id="4de5e-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="4de5e-113">Attribute</span></span>|<span data-ttu-id="4de5e-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4de5e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4de5e-115">türü</span><span class="sxs-lookup"><span data-stu-id="4de5e-115">type</span></span>|<span data-ttu-id="4de5e-116">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="4de5e-116">Required string attribute.</span></span><br /><br /> <span data-ttu-id="4de5e-117">Tür adını (ad alanı dahil), derleme adını, sürüm numarasını, kültürü ve ortak anahtar belirtecini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4de5e-117">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4de5e-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4de5e-118">Child Elements</span></span>  
  
|<span data-ttu-id="4de5e-119">Öğe</span><span class="sxs-lookup"><span data-stu-id="4de5e-119">Element</span></span>|<span data-ttu-id="4de5e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4de5e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4de5e-121">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="4de5e-121">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="4de5e-122">Eklenmekte olan, belirtilen tanımlı tür için bilinen türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="4de5e-122">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="4de5e-123">Belirtilen tür genel bir türse, bilinen türü döndürmek için hangi genel parametrenin kullanıldığını belirtmek üzere `<knownType>` öğesine bir parametre öğesi de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4de5e-123">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4de5e-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4de5e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="4de5e-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="4de5e-125">Element</span></span>|<span data-ttu-id="4de5e-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4de5e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4de5e-127">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="4de5e-127">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="4de5e-128">Tarafından seri durumundan çıkarma sırasında bilinen türler gerektiren türleri içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="4de5e-128">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4de5e-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4de5e-129">Remarks</span></span>  
 <span data-ttu-id="4de5e-130">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="4de5e-130">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="4de5e-131">Bu öğenin kullanılmasıyla ilgili bir örnek için bkz. [ DataContractSerializer>.\<](datacontractserializer-element.md)</span><span class="sxs-lookup"><span data-stu-id="4de5e-131">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4de5e-132"><xref:System.Object> Türü <xref:System.Configuration.ConfigurationErrorsException> olarak eklerseniz ,biroluşturulur.`<declaredType>`</span><span class="sxs-lookup"><span data-stu-id="4de5e-132">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="4de5e-133">Bunun nedeni <xref:System.Object> , türün yapılandırmada belirtilen bir tür olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4de5e-133">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4de5e-134">Örnek</span><span class="sxs-lookup"><span data-stu-id="4de5e-134">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4de5e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4de5e-135">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="4de5e-136">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="4de5e-136">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="4de5e-137">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="4de5e-137">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="4de5e-138">\<\<DeclaredTypes > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="4de5e-138">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
