---
title: <schemaImporterExtensions> için <add> Öğesi
description: <add>Öğesi, xsd türlerini .net türlerine eşlemek Için XmlSchemaImporter sınıfı tarafından kullanılan türleri ekler.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: b8a0775e9d33d59606b1150aa9a1b3b1026d4b0b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726450"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="5aa34-103">\<schemaImporterExtensions> için \<add> Öğesi</span><span class="sxs-lookup"><span data-stu-id="5aa34-103">\<add> Element for \<schemaImporterExtensions></span></span>

<span data-ttu-id="5aa34-104">, <xref:System.Xml.Serialization.XmlSchemaImporter> Xsd türlerini .net türlerine eşlemek için tarafından kullanılan türleri ekler.</span><span class="sxs-lookup"><span data-stu-id="5aa34-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET types.</span></span> <span data-ttu-id="5aa34-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="5aa34-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>  
  
\<configuration>  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
\<add>  
  
## <a name="syntax"></a><span data-ttu-id="5aa34-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5aa34-106">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5aa34-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5aa34-107">Attributes and Elements</span></span>  

 <span data-ttu-id="5aa34-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5aa34-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5aa34-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5aa34-109">Attributes</span></span>  
  
|<span data-ttu-id="5aa34-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5aa34-110">Attribute</span></span>|<span data-ttu-id="5aa34-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5aa34-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5aa34-112">**ada**</span><span class="sxs-lookup"><span data-stu-id="5aa34-112">**name**</span></span>|<span data-ttu-id="5aa34-113">Örnek bulmak için kullanılan basit bir ad.</span><span class="sxs-lookup"><span data-stu-id="5aa34-113">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="5aa34-114">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="5aa34-114">**type**</span></span>|<span data-ttu-id="5aa34-115">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="5aa34-115">Required.</span></span> <span data-ttu-id="5aa34-116">Eklemek için şema uzantısı sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5aa34-116">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="5aa34-117">**Tür** özniteliği değeri bir satırda olmalı ve tam nitelikli tür adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5aa34-117">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="5aa34-118">Derlemesi Genel Derleme Önbelleği'ne (GAC) yerleştirildiğinde, sürüm, kültür ve ortak anahtar belirteci imzalı derleme, aynı zamanda içermelidir.</span><span class="sxs-lookup"><span data-stu-id="5aa34-118">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5aa34-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5aa34-119">Child Elements</span></span>  

 <span data-ttu-id="5aa34-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="5aa34-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5aa34-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5aa34-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5aa34-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="5aa34-122">Element</span></span>|<span data-ttu-id="5aa34-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5aa34-123">Description</span></span>|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|<span data-ttu-id="5aa34-124">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="5aa34-124">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5aa34-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="5aa34-125">Example</span></span>  

 <span data-ttu-id="5aa34-126">Aşağıdaki kod örneğinde XmlSchemaImporter türleri eşlerken kullanabileceğiniz bir uzantı türü ekler.</span><span class="sxs-lookup"><span data-stu-id="5aa34-126">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <schemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a" />
    </schemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5aa34-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5aa34-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="5aa34-128">\<system.xml.serialization> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="5aa34-128">\<system.xml.serialization> Element</span></span>](system-xml-serialization-element.md)
- [<span data-ttu-id="5aa34-129">\<schemaImporterExtensions> Dosyalarında</span><span class="sxs-lookup"><span data-stu-id="5aa34-129">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
