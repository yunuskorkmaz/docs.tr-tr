---
title: <add> için <schemaImporterExtensions> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- <add> element for <schemaImporterExtensions> element
ms.assetid: c828a558-094b-441e-9065-790b87315fa0
ms.openlocfilehash: 89196b094d5631c9e243a51a718e53f9c06db20d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270569"
---
# <a name="add-element-for-schemaimporterextensions"></a>\<Ekle > öğesi için \<schemaImporterExtensions >
Tarafından kullanılan türleri ekler <xref:System.Xml.Serialization.XmlSchemaImporter> XSD türlerini .NET Framework türleriyle eşlemek için. Yapılandırma dosyaları hakkında daha fazla bilgi için bkz. [yapılandırma dosyası şeması](../../../docs/framework/configure-apps/file-schema/index.md).  
  
 \<Yapılandırma >  
\<system.xml.serialization>  
\<schemaImporterExtensions >  
\<Ekle >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<add name = "typeName" type="fully qualified type [,Version=version number] [,Culture=culture] [,PublicKeyToken= token]"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|**Adı**|Örnek bulmak için kullanılan basit bir ad.|  
|**type**|Gerekli. Eklemek için şema uzantısı sınıfını belirtir. **Türü** öznitelik değeri tek bir satırda ve gerekir tam tür adını içerir. Derlemesi Genel Derleme Önbelleği'ne (GAC) yerleştirildiğinde, sürüm, kültür ve ortak anahtar belirteci imzalı derleme, aynı zamanda içermelidir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|\<schemaImporterExtensions >|Tarafından kullanılan türler içerir <xref:System.Xml.Serialization.XmlSchemaImporter>.|  
  
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
- [\<system.xml.serialization> Element](../../../docs/standard/serialization/system-xml-serialization-element.md)
- [\<schemaImporterExtensions > öğesi](../../../docs/standard/serialization/schemaimporterextensions-element.md)
