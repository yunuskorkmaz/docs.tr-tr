---
title: "Özel öğe SingleTagSectionHandler için"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 496967bc3638344d2b39d428b85270b575b325ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="custom-element-for-singletagsectionhandler"></a>Özel öğe SingleTagSectionHandler için

Tarafından tanımlanan bir özel yapılandırma bölümünde ayarlarını tanımlayan bir <section> öğe ve kullandığı <xref:System.Configuration.SingleTagSectionHandler> sınıfı.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;*\<sectionName >*

## <a name="syntax"></a>Sözdizimi

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Öznitelikler

Kullanıcı tanımlı, öznitelikler ve öznitelik değerleri şunlardır.

## <a name="parent-element"></a>Üst öğesi

|     | Açıklama |
| --- | ----------- |
| [**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

**\<SectionName >** öğesidir tarafından tanımlanan bir özel bir [  **\<bölüm >** ](~/docs/framework/configure-apps/file-schema/section-element.md) içinde etiketi [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) öğesi. Yapılandırma sistemi döndüren bir <xref:System.Collections.IDictionary> nesne çağırdığınızda <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki örnek adlı özel bir öğe bildirir  **\<sampleSection >** tarafından okunur ayarları içeren <xref:System.Configuration.SingleTagSectionHandler> sınıfı:

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
