---
title: <system.xml.serialization> Öğesi
description: Bu makalede, XML serileştirmesini denetlemek için en üst düzey öğe olan System. xml. Serialization > öğesi < açıklanmaktadır.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: f69e80592e9321de64421b977a63b83d8be2ad9e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289492"
---
# <a name="systemxmlserialization-element"></a>\<system.xml.serialization> Öğesi

XML serileştirmesini denetlemek için en üst düzey öğe. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md).

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a>Sözdizimi

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt Öğeler

|Öğe|Description|
|-------------|-----------------|
|[\<dateTimeSerialization>Dosyalarında](datetimeserialization-element.md)|Serileştirme modu belirler <xref:System.DateTime> nesneleri.|
|[\<schemaImporterExtensions>Dosyalarında](schemaimporterextensions-element.md)|Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter> için .NET Framework türleri için XSD türü eşleme.|

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Description|
|-------------|-----------------|
|[\<configuration>Dosyalarında](../../framework/configure-apps/file-schema/configuration-element.md)|Her yapılandırma dosyasında ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir nesnenin serileştirme modunun <xref:System.DateTime> ve tarafından kullanılan türlerin <xref:System.Xml.Serialization.XmlSchemaImporter> .NET Framework türlerine ne zaman ekleneceğini gösterir.

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
- [\<dateTimeSerialization>Dosyalarında](datetimeserialization-element.md)
- [\<schemaImporterExtensions>Dosyalarında](schemaimporterextensions-element.md)
- [\<add>İçin öğesi\<schemaImporterExtensions>](add-element-for-schemaimporterextensions.md)
