---
description: 'Hakkında daha fazla bilgi edinin: <add> <declaredTypes> öğe'
title: <add><declaredTypes>öğesinin
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 8e2be6e553ee5dc5c96bcae81d1c1c6bf609afed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803990"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="92c0d-103">\<add>\<declaredTypes>öğesinin</span><span class="sxs-lookup"><span data-stu-id="92c0d-103">\<add> of \<declaredTypes> Element</span></span>

<span data-ttu-id="92c0d-104">Seri durumdan çıkarma sırasında tarafından kullanılan bir tür ekler <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="92c0d-104">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="92c0d-105">Her bir tanımlı tür, bir alan veya tanımlanmış türün özelliği olarak döndürülecek bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="92c0d-105">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="92c0d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="92c0d-106">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92c0d-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="92c0d-107">Attributes and Elements</span></span>  

 <span data-ttu-id="92c0d-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="92c0d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92c0d-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="92c0d-109">Attributes</span></span>  
  
|<span data-ttu-id="92c0d-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="92c0d-110">Attribute</span></span>|<span data-ttu-id="92c0d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c0d-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92c0d-112">tür</span><span class="sxs-lookup"><span data-stu-id="92c0d-112">type</span></span>|<span data-ttu-id="92c0d-113">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="92c0d-113">Required string attribute.</span></span><br /><br /> <span data-ttu-id="92c0d-114">Tür adını (ad alanı dahil), derleme adını, sürüm numarasını, kültürü ve ortak anahtar belirtecini belirtir.</span><span class="sxs-lookup"><span data-stu-id="92c0d-114">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92c0d-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="92c0d-115">Child Elements</span></span>  
  
|<span data-ttu-id="92c0d-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="92c0d-116">Element</span></span>|<span data-ttu-id="92c0d-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c0d-117">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="92c0d-118">Eklenmekte olan, belirtilen tanımlı tür için bilinen türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="92c0d-118">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="92c0d-119">Belirtilen tür genel bir türse, `<knownType>` bilinen türü döndürmek için hangi genel parametrenin kullanıldığını belirtmek üzere öğesine bir parametre öğesi de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="92c0d-119">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92c0d-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="92c0d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="92c0d-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="92c0d-121">Element</span></span>|<span data-ttu-id="92c0d-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92c0d-122">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="92c0d-123">Tarafından seri durumundan çıkarma sırasında bilinen türler gerektiren türleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="92c0d-123">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92c0d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92c0d-124">Remarks</span></span>  

 <span data-ttu-id="92c0d-125">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="92c0d-125">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="92c0d-126">[\<dataContractSerializer>](datacontractserializer-element.md)Bu öğenin kullanımıyla ilgili bir örnek için bkz..</span><span class="sxs-lookup"><span data-stu-id="92c0d-126">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92c0d-127"><xref:System.Object>Türü olarak eklerseniz `<declaredType>` , bir oluşturulur <xref:System.Configuration.ConfigurationErrorsException> .</span><span class="sxs-lookup"><span data-stu-id="92c0d-127">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="92c0d-128">Bunun nedeni, <xref:System.Object> türün yapılandırmada belirtilen bir tür olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="92c0d-128">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92c0d-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="92c0d-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92c0d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92c0d-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="92c0d-131">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="92c0d-131">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="92c0d-132">\<add> durumunu \<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="92c0d-132">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
