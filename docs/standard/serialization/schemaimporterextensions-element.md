---
title: <schemaImporterExtensions> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5ed80ac370e34d6b62bb2b601cb7bd978228a302
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159825"
---
# <a name="schemaimporterextensions-element"></a>\<SchemaImporterExtensions> öğesi
Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<SchemaImporterExtensions \<Için> öğesi ekleme>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)|Eşlemeleri oluşturmak <xref:System.Xml.Serialization.XmlSchemaImporter> için tarafından kullanılan türleri ekler.|  
  
## <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<System. xml. Serialization> öğesi](../../../docs/standard/serialization/system-xml-serialization-element.md)|XML serileştirmesini denetlemek için en üst düzey öğe.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.Xml.Serialization.XmlSchemaImporter> .NET Framework türlerine xsd türleri eşlerken tarafından kullanılan türlerin nasıl ekleneceğini göstermektedir.  
  
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
- [Yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> öğesi](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<SchemaImporterExtensions \<Için> öğesi ekleme>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
- [\<System. xml. Serialization> öğesi](../../../docs/standard/serialization/system-xml-serialization-element.md)
