---
title: XML Veri Türlerini CLR Türleriyle Eşleme
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: cabdfcad-f359-479b-b71c-8b2fad42ca49
ms.openlocfilehash: f14c8d961fe0934b8e843c39a217e7c2db8237c3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289115"
---
# <a name="mapping-xml-data-types-to-clr-types"></a>XML Veri Türlerini CLR Türleriyle Eşleme

Aşağıdaki tabloda, XML veri türleri ve ortak dil çalışma zamanı (CLR) türleri arasındaki varsayılan eşleme açıklanmaktadır.

> [!NOTE]
> `xs`Ve `xdt` ön ekler <https://www.w3.org/2001/XMLSchema> <https://www.w3.org/2003/05/xpath-datatypes> sırasıyla ve ad alanı URI 'leri ile eşleştirilir.

|XML türü|CLR türü|
|--------------|--------------|
|`xs:anyURI`|<xref:System.Uri>|
|`xs:base64Binary`|`Byte[]`|
|`xs:boolean`|<xref:System.Boolean>|
|`xs:byte`|<xref:System.SByte>|
|`xs:date`|<xref:System.DateTime>|
|`xs:dateTime`|<xref:System.DateTime>|
|`xs:decimal`|<xref:System.Decimal>|
|`xs:double`|<xref:System.Double>|
|`xs:duration`|<xref:System.TimeSpan>|
|`xs:ENTITIES`|`String[]`|
|`xs:ENTITY`|<xref:System.String>|
|`xs:float`|<xref:System.Single>|
|`xs:gDay`|<xref:System.DateTime>|
|`xs:gMonthDay`|<xref:System.DateTime>|
|`xs:gYear`|<xref:System.DateTime>|
|`xs:gYearMonth`|<xref:System.DateTime>|
|`xs:hexBinary`|`Byte[]`|
|`xs:ID`|<xref:System.String>|
|`xs:IDREF`|<xref:System.String>|
|`xs:IDREFS`|`String[]`|
|`xs:int`|<xref:System.Int32>|
|`xs:integer`|<xref:System.Decimal>|
|`xs:language`|<xref:System.String>|
|`xs:long`|<xref:System.Int64>|
|`xs:gMonth`|<xref:System.DateTime>|
|`xs:Name`|<xref:System.String>|
|`xs:NCName`|<xref:System.String>|
|`xs:negativeInteger`|<xref:System.Decimal>|
|`xs:NMTOKEN`|<xref:System.String>|
|`xs:NMTOKENS`|`String[]`|
|`xs:nonNegativeInteger`|<xref:System.Decimal>|
|`xs:nonPositiveInteger`|<xref:System.Decimal>|
|`xs:normalizedString`|<xref:System.String>|
|`xs:NOTATION`|<xref:System.Xml.XmlQualifiedName>|
|`xs:positiveInteger`|<xref:System.Decimal>|
|`xs:QName`|<xref:System.Xml.XmlQualifiedName>|
|`xs:short`|<xref:System.Int16>|
|`xs:string`|<xref:System.String>|
|`xs:time`|<xref:System.DateTime>|
|`xs:token`|<xref:System.String>|
|`xs:unsignedByte`|<xref:System.Byte>|
|`xs:unsignedInt`|<xref:System.UInt32>|
|`xs:unsignedLong`|<xref:System.UInt64>|
|`xs:unsignedShort`|<xref:System.UInt16>|
|`xdt:dayTimeDuration`|<xref:System.TimeSpan>|
|`xdt:yearMonthDuration`|<xref:System.TimeSpan>|
|`xdt:untypedAtomic`|<xref:System.String>|
|`xdt:anyAtomicType`|<xref:System.Object>|
|`xs:anySimpleType`|<xref:System.String>|
|Belge düğümü|<xref:System.Xml.XPath.XPathNavigator>|
|Öğe düğümü|<xref:System.Xml.XPath.XPathNavigator>|
|Öznitelik düğümü|<xref:System.Xml.XPath.XPathNavigator>|
|Ad alanı düğümü|<xref:System.Xml.XPath.XPathNavigator>|
|Metin düğümü|<xref:System.Xml.XPath.XPathNavigator>|
|Açıklama düğümü|<xref:System.Xml.XPath.XPathNavigator>|
|Yönerge düğümü işleniyor|<xref:System.Xml.XPath.XPathNavigator>|

## <a name="see-also"></a>Ayrıca bkz.

- [System.Xml Sınıflarında Tür Desteği](type-support-in-the-system-xml-classes.md)
