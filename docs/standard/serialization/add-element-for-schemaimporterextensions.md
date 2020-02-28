---
title: <add> için <schemaImporterExtensions> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 4f47623aa305ae6e98625acc3d199a76e27d2ea5
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159942"
---
# <a name="add-element-for-schemaimporterextensions"></a><span data-ttu-id="19f8d-102">\<SchemaImporterExtensions için > öğesi \<ekleyin ></span><span class="sxs-lookup"><span data-stu-id="19f8d-102">\<add> Element for \<schemaImporterExtensions></span></span>
<span data-ttu-id="19f8d-103">Tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> XSD türlerini .NET Framework türleriyle eşlemek için.</span><span class="sxs-lookup"><span data-stu-id="19f8d-103">Adds types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping XSD types to .NET Framework types.</span></span> <span data-ttu-id="19f8d-104">Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="19f8d-104">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="19f8d-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="19f8d-105">\<configuration></span></span>  
<span data-ttu-id="19f8d-106">System. xml. Serialization > \<</span><span class="sxs-lookup"><span data-stu-id="19f8d-106">\<system.xml.serialization></span></span>  
<span data-ttu-id="19f8d-107">\<SchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="19f8d-107">\<schemaImporterExtensions></span></span>  
<span data-ttu-id="19f8d-108">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="19f8d-108">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19f8d-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19f8d-109">Syntax</span></span>  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19f8d-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="19f8d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="19f8d-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="19f8d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19f8d-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="19f8d-112">Attributes</span></span>  
  
|<span data-ttu-id="19f8d-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="19f8d-113">Attribute</span></span>|<span data-ttu-id="19f8d-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19f8d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19f8d-115">**ada**</span><span class="sxs-lookup"><span data-stu-id="19f8d-115">**name**</span></span>|<span data-ttu-id="19f8d-116">Örnek bulmak için kullanılan basit bir ad.</span><span class="sxs-lookup"><span data-stu-id="19f8d-116">A simple name that is used to find the instance.</span></span>|  
|<span data-ttu-id="19f8d-117">**type**</span><span class="sxs-lookup"><span data-stu-id="19f8d-117">**type**</span></span>|<span data-ttu-id="19f8d-118">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="19f8d-118">Required.</span></span> <span data-ttu-id="19f8d-119">Eklemek için şema uzantısı sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="19f8d-119">Specifies the schema  extension class to add.</span></span> <span data-ttu-id="19f8d-120">**Tür** özniteliği değeri bir satırda olmalı ve tam nitelikli tür adını içermelidir.</span><span class="sxs-lookup"><span data-stu-id="19f8d-120">The **type** attribute value must be on one line, and include the fully qualified type name.</span></span> <span data-ttu-id="19f8d-121">Derlemesi Genel Derleme Önbelleği'ne (GAC) yerleştirildiğinde, sürüm, kültür ve ortak anahtar belirteci imzalı derleme, aynı zamanda içermelidir.</span><span class="sxs-lookup"><span data-stu-id="19f8d-121">When the assembly is placed in the Global Assembly Cache (GAC), it must also include the version, culture, and public key token of the signed assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19f8d-122">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="19f8d-122">Child Elements</span></span>  
 <span data-ttu-id="19f8d-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="19f8d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19f8d-124">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="19f8d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="19f8d-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="19f8d-125">Element</span></span>|<span data-ttu-id="19f8d-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19f8d-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19f8d-127">\<SchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="19f8d-127">\<schemaImporterExtensions></span></span>|<span data-ttu-id="19f8d-128">Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter>.</span><span class="sxs-lookup"><span data-stu-id="19f8d-128">Contains the types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="19f8d-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="19f8d-129">Example</span></span>  
 <span data-ttu-id="19f8d-130">Aşağıdaki kod örneğinde XmlSchemaImporter türleri eşlerken kullanabileceğiniz bir uzantı türü ekler.</span><span class="sxs-lookup"><span data-stu-id="19f8d-130">The following code example adds an extension type that the XmlSchemaImporter can use when mapping types.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19f8d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19f8d-131">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [<span data-ttu-id="19f8d-132">System. xml. Serialization > öğesi \<</span><span class="sxs-lookup"><span data-stu-id="19f8d-132">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [<span data-ttu-id="19f8d-133">\<SchemaImporterExtensions > öğesi</span><span class="sxs-lookup"><span data-stu-id="19f8d-133">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
