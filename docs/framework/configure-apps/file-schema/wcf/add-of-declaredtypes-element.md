---
title: <add><declaredTypes> öğesinin
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: a001e8743b2c24f68b1b23cbccf3e5ac162c4e71
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400652"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="0c326-102">\<\<DeclaredTypes > öğesinin > ekleyin</span><span class="sxs-lookup"><span data-stu-id="0c326-102">\<add> of \<declaredTypes> Element</span></span>
<span data-ttu-id="0c326-103">Seri durumdan çıkarma <xref:System.Runtime.Serialization.DataContractSerializer> sırasında tarafından kullanılan bir tür ekler.</span><span class="sxs-lookup"><span data-stu-id="0c326-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="0c326-104">Her bir tanımlı tür, bir alan veya tanımlanmış türün özelliği olarak döndürülecek bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0c326-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
<span data-ttu-id="0c326-105">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0c326-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0c326-106">&nbsp;&nbsp;[ **\<System. Runtime. Serialization >** ](system-runtime-serialization.md)</span><span class="sxs-lookup"><span data-stu-id="0c326-106">&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)</span></span>\
<span data-ttu-id="0c326-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dataContractSerializer >** ](datacontractserializer.md)</span><span class="sxs-lookup"><span data-stu-id="0c326-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)</span></span>\
<span data-ttu-id="0c326-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<declaredTypes >** ](declaredtypes.md)</span><span class="sxs-lookup"><span data-stu-id="0c326-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)</span></span>\
<span data-ttu-id="0c326-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="0c326-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c326-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c326-110">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c326-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c326-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0c326-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0c326-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c326-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0c326-113">Attributes</span></span>  
  
|<span data-ttu-id="0c326-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0c326-114">Attribute</span></span>|<span data-ttu-id="0c326-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c326-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0c326-116">türü</span><span class="sxs-lookup"><span data-stu-id="0c326-116">type</span></span>|<span data-ttu-id="0c326-117">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0c326-117">Required string attribute.</span></span><br /><br /> <span data-ttu-id="0c326-118">Tür adını (ad alanı dahil), derleme adını, sürüm numarasını, kültürü ve ortak anahtar belirtecini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c326-118">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c326-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c326-119">Child Elements</span></span>  
  
|<span data-ttu-id="0c326-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c326-120">Element</span></span>|<span data-ttu-id="0c326-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c326-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c326-122">\<knownType ></span><span class="sxs-lookup"><span data-stu-id="0c326-122">\<knownType></span></span>](knowntype.md)|<span data-ttu-id="0c326-123">Eklenmekte olan, belirtilen tanımlı tür için bilinen türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c326-123">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="0c326-124">Belirtilen tür genel bir türse, bilinen türü döndürmek için hangi genel parametrenin kullanıldığını belirtmek üzere `<knownType>` öğesine bir parametre öğesi de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c326-124">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c326-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0c326-125">Parent Elements</span></span>  
  
|<span data-ttu-id="0c326-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="0c326-126">Element</span></span>|<span data-ttu-id="0c326-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c326-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c326-128">\<declaredTypes ></span><span class="sxs-lookup"><span data-stu-id="0c326-128">\<declaredTypes></span></span>](declaredtypes.md)|<span data-ttu-id="0c326-129">Tarafından seri durumundan çıkarma sırasında bilinen türler gerektiren türleri içerir <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0c326-129">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c326-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c326-130">Remarks</span></span>  
 <span data-ttu-id="0c326-131">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="0c326-131">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="0c326-132">Bu öğenin kullanılmasıyla ilgili bir örnek için bkz. [ DataContractSerializer>.\<](datacontractserializer-element.md)</span><span class="sxs-lookup"><span data-stu-id="0c326-132">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c326-133"><xref:System.Object> Türü <xref:System.Configuration.ConfigurationErrorsException> olarak eklerseniz ,biroluşturulur.`<declaredType>`</span><span class="sxs-lookup"><span data-stu-id="0c326-133">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="0c326-134">Bunun nedeni <xref:System.Object> , türün yapılandırmada belirtilen bir tür olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0c326-134">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c326-135">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c326-135">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0c326-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c326-136">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="0c326-137">Veri Anlaşması Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="0c326-137">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [<span data-ttu-id="0c326-138">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="0c326-138">\<dataContractSerializer></span></span>](datacontractserializer-element.md)
- [<span data-ttu-id="0c326-139">\<\<DeclaredTypes > > ekleyin</span><span class="sxs-lookup"><span data-stu-id="0c326-139">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
