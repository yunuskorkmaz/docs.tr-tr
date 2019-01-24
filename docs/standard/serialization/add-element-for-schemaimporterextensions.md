---
title: '&lt;ekleme&gt; öğesi için &lt;schemaImporterExtensions&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 212ce43dc50735da71091111a0fd03eca0583315
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577691"
---
# <a name="ltaddgt-element-for-ltschemaimporterextensionsgt"></a><span data-ttu-id="d4261-102">&lt;ekleme&gt; öğesi için &lt;schemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="d4261-102">&lt;add&gt; Element for &lt;schemaImporterExtensions&gt;</span></span>
<span data-ttu-id="d4261-103">Tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> XSD türlerini .NET Framework türleriyle eşlemek için.</span><span class="sxs-lookup"><span data-stu-id="d4261-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="d4261-104">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="d4261-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="d4261-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="d4261-105">\<configuration></span></span>  
<span data-ttu-id="d4261-106">\<system.xml.serialization></span><span class="sxs-lookup"><span data-stu-id="d4261-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="d4261-107">\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="d4261-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="d4261-108">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d4261-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4261-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4261-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4261-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4261-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d4261-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d4261-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4261-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d4261-112">Attributes</span></span>  
  
|<span data-ttu-id="d4261-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d4261-113">Attribute</span></span>|<span data-ttu-id="d4261-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4261-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4261-115">**Adı**</span><span class="sxs-lookup"><span data-stu-id="d4261-115">**name**</span></span>|<span data-ttu-id="d4261-116">Örnek bulmak için kullanılan basit bir ad.</span><span class="sxs-lookup"><span data-stu-id="d4261-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="d4261-117">**type**</span><span class="sxs-lookup"><span data-stu-id="d4261-117">**type**</span></span>|<span data-ttu-id="d4261-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="d4261-118">Required.</span></span> <span data-ttu-id="d4261-119">Eklemek için şema uzantısı sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d4261-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="d4261-120">**Türü** öznitelik değeri tek bir satırda ve gerekir tam tür adını içerir.</span><span class="sxs-lookup"><span data-stu-id="d4261-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="d4261-121">Derlemesi Genel Derleme Önbelleği'ne (GAC) yerleştirildiğinde, sürüm, kültür ve ortak anahtar belirteci imzalı derleme, aynı zamanda içermelidir.</span><span class="sxs-lookup"><span data-stu-id="d4261-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4261-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4261-122">Child Elements</span></span>  
 <span data-ttu-id="d4261-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="d4261-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4261-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d4261-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d4261-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="d4261-125">Element</span></span>|<span data-ttu-id="d4261-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4261-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4261-127">\<schemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="d4261-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="d4261-128">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="d4261-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d4261-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="d4261-129">Example</span></span>  
 <span data-ttu-id="d4261-130">Aşağıdaki kod örneğinde XmlSchemaImporter türleri eşlerken kullanabileceğiniz bir uzantı türü ekler.</span><span class="sxs-lookup"><span data-stu-id="d4261-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d4261-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4261-131">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="d4261-132">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="d4261-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="d4261-133">\<schemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="d4261-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
