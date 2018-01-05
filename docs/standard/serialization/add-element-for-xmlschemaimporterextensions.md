---
title: "&lt;ekleme&gt; öğesi için &lt;xmlSchemaImporterExtensions&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <xmlSchemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dc01f0ed6b5b1bac5131e6262db5d3a2847a65ab
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="ltaddgt-element-for-ltxmlschemaimporterextensionsgt"></a><span data-ttu-id="3dc69-102">&lt;ekleme&gt; öğesi için &lt;xmlSchemaImporterExtensions&gt;</span><span class="sxs-lookup"><span data-stu-id="3dc69-102">&lt;add&gt; Element for &lt;xmlSchemaImporterExtensions&gt;</span></span>
<span data-ttu-id="3dc69-103">Tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> XSD türlerini .NET Framework türleriyle eşlemek için.</span><span class="sxs-lookup"><span data-stu-id="3dc69-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="3dc69-104">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz: [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="3dc69-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="3dc69-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="3dc69-105">\<configuration></span></span>  
<span data-ttu-id="3dc69-106">\<dizileştirme mekanizmasını System.xml.Serialization ></span><span class="sxs-lookup"><span data-stu-id="3dc69-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="3dc69-107">\<XmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="3dc69-107">\<XmlSchemaImporterExtensions></span></span>  
<span data-ttu-id="3dc69-108">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="3dc69-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dc69-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3dc69-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3dc69-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3dc69-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3dc69-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3dc69-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3dc69-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3dc69-112">Attributes</span></span>  
  
|<span data-ttu-id="3dc69-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="3dc69-113">Attribute</span></span>|<span data-ttu-id="3dc69-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3dc69-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3dc69-115">**adı**</span><span class="sxs-lookup"><span data-stu-id="3dc69-115">**name**</span></span>|<span data-ttu-id="3dc69-116">Örnek bulmak için kullanılan basit bir ad.</span><span class="sxs-lookup"><span data-stu-id="3dc69-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="3dc69-117">**türü**</span><span class="sxs-lookup"><span data-stu-id="3dc69-117">**type**</span></span>|<span data-ttu-id="3dc69-118">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="3dc69-118">Required.</span></span> <span data-ttu-id="3dc69-119">Eklemek için şema uzantısı sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3dc69-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="3dc69-120">**Türü** öznitelik değeri tek bir satırda ve gerekir tam olarak nitelenmiş tür adını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="3dc69-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="3dc69-121">Derlemesi Genel Derleme Önbelleği'ne (GAC) yerleştirildiğinde, sürüm, kültür ve ortak anahtar belirteci imzalı derleme, aynı zamanda içermelidir.</span><span class="sxs-lookup"><span data-stu-id="3dc69-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3dc69-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3dc69-122">Child Elements</span></span>  
 <span data-ttu-id="3dc69-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="3dc69-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3dc69-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3dc69-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3dc69-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="3dc69-125">Element</span></span>|<span data-ttu-id="3dc69-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3dc69-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3dc69-127">\<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="3dc69-127">\<xmlSchemaImporterExtensions></span></span>|<span data-ttu-id="3dc69-128">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="3dc69-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3dc69-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="3dc69-129">Example</span></span>  
 <span data-ttu-id="3dc69-130">Aşağıdaki kod örneğinde XmlSchemaImporter türleri eşlerken kullanabileceğiniz bir uzantı türü ekler.</span><span class="sxs-lookup"><span data-stu-id="3dc69-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
```xml  
<configuration>  
  <system.xml.serialization>  
    <xmlSchemaImporterExtensions>  
       <add name="contoso" type="System.Web.Mobile.MobileCapabilities,   
       System.Web.Mobile, Version=2.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a" />   
    </xmlSchemaImporterExtensions>  
  </system.xml.serialization>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3dc69-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3dc69-131">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 [<span data-ttu-id="3dc69-132">\<dizileştirme mekanizmasını System.xml.Serialization > öğesi</span><span class="sxs-lookup"><span data-stu-id="3dc69-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 [<span data-ttu-id="3dc69-133">\<schemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="3dc69-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
