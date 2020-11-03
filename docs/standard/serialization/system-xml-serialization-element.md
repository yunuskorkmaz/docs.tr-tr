---
title: <system.xml.serialization> Öğesi
description: Bu makalede, XML serileştirmesini denetlemek için en üst düzey öğe olan <system.xml. Serialization> öğesi açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 6291799aadc429e943996f2256d773ac36dd370f
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282392"
---
# <a name="systemxmlserialization-element"></a>\<system.xml.serialization> Öğesi

XML serileştirmesini denetlemek için en üst düzey öğe. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md).

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a>Syntax

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<dateTimeSerialization> Dosyalarında](datetimeserialization-element.md)|Serileştirme modu belirler <xref:System.DateTime> nesneleri.|
|[\<schemaImporterExtensions> Dosyalarında](schemaimporterextensions-element.md)|<xref:System.Xml.Serialization.XmlSchemaImporter>XSD türlerinin .net türlerine eşlenmesi için tarafından kullanılan türleri içerir.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<configuration> Dosyalarında](../../framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir nesnenin serileştirme modunun <xref:System.DateTime> ve tarafından kullanılan türlerin ek olarak, <xref:System.Xml.Serialization.XmlSchemaImporter> xsd türlerini .net türlerine eşlerken nasıl ekleneceğini gösterir.

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [Yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> Dosyalarında](datetimeserialization-element.md)
- [\<schemaImporterExtensions> Dosyalarında](schemaimporterextensions-element.md)
- [\<add> İçin öğesi \<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
