---
title: <schemaImporterExtensions> Öğesi
description: <schemaImporterExtensions>Öğesi, xsd türlerinin .NET Framework türlerine eşlenmesi Için XmlSchemaImporter tarafından kullanılan türleri içerir.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: c46c5cb6e01463723f0f2ce3873fb4a6ec0b4e60
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84278408"
---
# <a name="schemaimporterextensions-element"></a>\<schemaImporterExtensions> Öğesi
Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<add>İçin öğesi\<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)|Eşlemeleri oluşturmak için tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> .|  
  
## <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<system.xml.serialization>Dosyalarında](system-xml-serialization-element.md)|XML serileştirmesini denetlemek için en üst düzey öğe.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Xml.Serialization.XmlSchemaImporter> .NET Framework TÜRLERINE xsd türleri eşlerken tarafından kullanılan türlerin nasıl ekleneceğini göstermektedir.  
  
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
- [\<dateTimeSerialization>Dosyalarında](datetimeserialization-element.md)
- [\<add>İçin öğesi\<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
- [\<system.xml.serialization>Dosyalarında](system-xml-serialization-element.md)
