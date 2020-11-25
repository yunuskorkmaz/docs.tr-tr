---
title: <schemaImporterExtensions> için <add> Öğesi
description: <add>Öğesi, xsd türlerini .net türlerine eşlemek Için XmlSchemaImporter sınıfı tarafından kullanılan türleri ekler.
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: b8a0775e9d33d59606b1150aa9a1b3b1026d4b0b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726450"
---
# <a name="add-element-for-schemaimporterextensions"></a>\<schemaImporterExtensions> için \<add> Öğesi

, <xref:System.Xml.Serialization.XmlSchemaImporter> Xsd türlerini .net türlerine eşlemek için tarafından kullanılan türleri ekler. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../framework/configure-apps/file-schema/index.md).  
  
\<configuration>  
\<system.xml.serialization>  
\<schemaImporterExtensions>  
\<add>  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**ada**|Örnek bulmak için kullanılan basit bir ad.|  
|**türüyle**|Gereklidir. Eklemek için şema uzantısı sınıfını belirtir. **Tür** özniteliği değeri bir satırda olmalı ve tam nitelikli tür adını içermelidir. Derlemesi Genel Derleme Önbelleği'ne (GAC) yerleştirildiğinde, sürüm, kültür ve ortak anahtar belirteci imzalı derleme, aynı zamanda içermelidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<schemaImporterExtensions>|Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter>.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod örneğinde XmlSchemaImporter türleri eşlerken kullanabileceğiniz bir uzantı türü ekler.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- [\<system.xml.serialization> Dosyalarında](system-xml-serialization-element.md)
- [\<schemaImporterExtensions> Dosyalarında](schemaimporterextensions-element.md)
