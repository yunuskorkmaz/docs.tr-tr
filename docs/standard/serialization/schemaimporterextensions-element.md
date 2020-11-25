---
title: <schemaImporterExtensions> Öğesi
description: <schemaImporterExtensions>Öğesi, xsd türlerini .net türlerine eşlemek Için XmlSchemaImporter tarafından kullanılan türleri içerir.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 6b644ed1112b748be4dd301d6fa6f2a6416dc67e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722147"
---
# <a name="schemaimporterextensions-element"></a>\<schemaImporterExtensions> öğesi

<xref:System.Xml.Serialization.XmlSchemaImporter>XSD türlerinin .net türlerine eşlenmesi için tarafından kullanılan türleri içerir. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md).  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<add> İçin öğesi \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)|Eşlemeleri oluşturmak için tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> .|  
  
## <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.xml.serialization> Dosyalarında](system-xml-serialization-element.md)|XML serileştirmesini denetlemek için en üst düzey öğe.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneği, <xref:System.Xml.Serialization.XmlSchemaImporter> xsd türlerini .net türlerine eşlerken tarafından kullanılan türlerin nasıl ekleneceğini göstermektedir.  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> Dosyalarında](datetimeserialization-element.md)
- [\<add> İçin öğesi \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization> Dosyalarında](system-xml-serialization-element.md)
