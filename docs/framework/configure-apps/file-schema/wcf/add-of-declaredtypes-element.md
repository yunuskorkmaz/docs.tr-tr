---
title: <add><declaredTypes>öğesinin
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 9af47848b03074ec88f38a5884089bc50239ee50
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201674"
---
# <a name="add-of-declaredtypes-element"></a><span data-ttu-id="579d2-102">\<add>\<declaredTypes>öğesinin</span><span class="sxs-lookup"><span data-stu-id="579d2-102">\<add> of \<declaredTypes> Element</span></span>

<span data-ttu-id="579d2-103">Seri durumdan çıkarma sırasında tarafından kullanılan bir tür ekler <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="579d2-103">Adds a type used by the <xref:System.Runtime.Serialization.DataContractSerializer> during deserialization.</span></span> <span data-ttu-id="579d2-104">Her bir tanımlı tür, bir alan veya tanımlanmış türün özelliği olarak döndürülecek bilinen türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="579d2-104">Each declared type includes the known types that will be returned as a field or property of the declared type.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.serialization>**](system-runtime-serialization.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<dataContractSerializer>**](datacontractserializer.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<declaredTypes>**](declaredtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="579d2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="579d2-105">Syntax</span></span>  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="579d2-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="579d2-106">Attributes and Elements</span></span>  

 <span data-ttu-id="579d2-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="579d2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="579d2-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="579d2-108">Attributes</span></span>  
  
|<span data-ttu-id="579d2-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="579d2-109">Attribute</span></span>|<span data-ttu-id="579d2-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="579d2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="579d2-111">tür</span><span class="sxs-lookup"><span data-stu-id="579d2-111">type</span></span>|<span data-ttu-id="579d2-112">Gerekli dize özniteliği.</span><span class="sxs-lookup"><span data-stu-id="579d2-112">Required string attribute.</span></span><br /><br /> <span data-ttu-id="579d2-113">Tür adını (ad alanı dahil), derleme adını, sürüm numarasını, kültürü ve ortak anahtar belirtecini belirtir.</span><span class="sxs-lookup"><span data-stu-id="579d2-113">Specifies the type name (including namespace), assembly name, version number, culture, and public key token.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="579d2-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="579d2-114">Child Elements</span></span>  
  
|<span data-ttu-id="579d2-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="579d2-115">Element</span></span>|<span data-ttu-id="579d2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="579d2-116">Description</span></span>|  
|-------------|-----------------|  
|[\<knownType>](knowntype.md)|<span data-ttu-id="579d2-117">Eklenmekte olan, belirtilen tanımlı tür için bilinen türü belirtir.</span><span class="sxs-lookup"><span data-stu-id="579d2-117">Specifies the known type for the declared type that is being added.</span></span> <span data-ttu-id="579d2-118">Belirtilen tür genel bir türse, `<knownType>` bilinen türü döndürmek için hangi genel parametrenin kullanıldığını belirtmek üzere öğesine bir parametre öğesi de eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="579d2-118">If the declared type is a generic type, then you must also add a parameter element to the `<knownType>` element to specify which generic parameter is used to return the known type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="579d2-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="579d2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="579d2-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="579d2-120">Element</span></span>|<span data-ttu-id="579d2-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="579d2-121">Description</span></span>|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|<span data-ttu-id="579d2-122">Tarafından seri durumundan çıkarma sırasında bilinen türler gerektiren türleri içerir <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="579d2-122">Contains the types that require known types during deserialization by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="579d2-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="579d2-123">Remarks</span></span>  

 <span data-ttu-id="579d2-124">Bilinen türler hakkında daha fazla bilgi için bkz. [veri sözleşmesi bilinen türler](../../../wcf/feature-details/data-contract-known-types.md) ve <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="579d2-124">For more information about known types, see [Data Contract Known Types](../../../wcf/feature-details/data-contract-known-types.md) and <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="579d2-125">[\<dataContractSerializer>](datacontractserializer-element.md)Bu öğenin kullanımıyla ilgili bir örnek için bkz..</span><span class="sxs-lookup"><span data-stu-id="579d2-125">See the [\<dataContractSerializer>](datacontractserializer-element.md) for an example of using this element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="579d2-126"><xref:System.Object>Türü olarak eklerseniz `<declaredType>` , bir oluşturulur <xref:System.Configuration.ConfigurationErrorsException> .</span><span class="sxs-lookup"><span data-stu-id="579d2-126">If you add the <xref:System.Object> type as a `<declaredType>`, a <xref:System.Configuration.ConfigurationErrorsException> is thrown.</span></span> <span data-ttu-id="579d2-127">Bunun nedeni, <xref:System.Object> türün yapılandırmada belirtilen bir tür olarak kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="579d2-127">This is because the <xref:System.Object> type cannot be used as a declared type in configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="579d2-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="579d2-128">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="579d2-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="579d2-129">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [<span data-ttu-id="579d2-130">Veri Sözleşmesi Bilinen Türler</span><span class="sxs-lookup"><span data-stu-id="579d2-130">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [<span data-ttu-id="579d2-131">\<add> durumunu \<declaredTypes></span><span class="sxs-lookup"><span data-stu-id="579d2-131">\<add> of \<declaredTypes></span></span>](add-of-declaredtypes-element.md)
