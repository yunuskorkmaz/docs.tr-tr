---
title: <schemaImporterExtensions> için <add> öğesi
description: <add>Öğesi, xsd türlerini .NET Framework türlerine eşlemek Için XmlSchemaImporter sınıfı tarafından kullanılan türleri ekler.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 401d1ba9cc2f97e93d7851f96f73b552e6ed6356
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378475"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="cb19c-103">\<\<SchemaImporterExtensions için> öğesi ekleme></span><span class="sxs-lookup"><span data-stu-id="cb19c-103">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="cb19c-104">Tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> XSD türlerini .NET Framework türleriyle eşlemek için.</span><span class="sxs-lookup"><span data-stu-id="cb19c-104">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="cb19c-105">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="cb19c-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="cb19c-106">\<yapılandırma></span><span class="sxs-lookup"><span data-stu-id="cb19c-106">\<configuration></span></span>  
<span data-ttu-id="cb19c-107">\<System. xml. Serialization></span><span class="sxs-lookup"><span data-stu-id="cb19c-107">\<system.xml.serialization></span></span>  
<span data-ttu-id="cb19c-108">\<SchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="cb19c-108">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="cb19c-109">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="cb19c-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb19c-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb19c-110">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb19c-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb19c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cb19c-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb19c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb19c-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="cb19c-113">Attributes</span></span>  
  
|<span data-ttu-id="cb19c-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="cb19c-114">Attribute</span></span>|<span data-ttu-id="cb19c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb19c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cb19c-116">**ada**</span><span class="sxs-lookup"><span data-stu-id="cb19c-116">**name**</span></span>|<span data-ttu-id="cb19c-117">Örnek bulmak için kullanılan basit bir ad.</span><span class="sxs-lookup"><span data-stu-id="cb19c-117">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="cb19c-118">**türüyle**</span><span class="sxs-lookup"><span data-stu-id="cb19c-118">**type**</span></span>|<span data-ttu-id="cb19c-119">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="cb19c-119">Required.</span></span> <span data-ttu-id="cb19c-120">Eklemek için şema uzantısı sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="cb19c-120">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="cb19c-121">**Tür** özniteliği değeri bir satırda olmalı ve tam nitelikli tür adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="cb19c-121">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="cb19c-122">Derlemesi Genel Derleme Önbelleği'ne (GAC) yerleştirildiğinde, sürüm, kültür ve ortak anahtar belirteci imzalı derleme, aynı zamanda içermelidir.</span><span class="sxs-lookup"><span data-stu-id="cb19c-122">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb19c-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb19c-123">Child Elements</span></span>  
 <span data-ttu-id="cb19c-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="cb19c-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb19c-125">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="cb19c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cb19c-126">Öğe</span><span class="sxs-lookup"><span data-stu-id="cb19c-126">Element</span></span>|<span data-ttu-id="cb19c-127">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb19c-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb19c-128">\<SchemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="cb19c-128">\<schemaImporterExtensions></span></span>|<span data-ttu-id="cb19c-129">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="cb19c-129">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cb19c-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb19c-130">Example</span></span>  
 <span data-ttu-id="cb19c-131">Aşağıdaki kod örneğinde XmlSchemaImporter türleri eşlerken kullanabileceğiniz bir uzantı türü ekler.</span><span class="sxs-lookup"><span data-stu-id="cb19c-131">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cb19c-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb19c-132">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="cb19c-133">\<System. xml. Serialization> öğesi</span><span class="sxs-lookup"><span data-stu-id="cb19c-133">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="cb19c-134">\<SchemaImporterExtensions> öğesi</span><span class="sxs-lookup"><span data-stu-id="cb19c-134">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
