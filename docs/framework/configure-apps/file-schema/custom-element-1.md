---
title: Singletagsectionhandler özel öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bfc2a916e37ac27d45746eb268912b3752f4d80f
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464443"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Singletagsectionhandler özel öğesi

Ayarları tarafından tanımlanan özel bir yapılandırma bölümünü tanımlayan bir \<bölüm > öğesi ve kullanımları <xref:System.Configuration.SingleTagSectionHandler> sınıfı.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;*\<sectionName >*

## <a name="syntax"></a>Sözdizimi

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Öznitelikler

Kullanıcı tanımlı öznitelikler ve öznitelik değerleri var.

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

 **\<SectionName >** öğedir tarafından tanımlanan özel bir öğe bir [  **\<bölüm >** ](~/docs/framework/configure-apps/file-schema/section-element.md) içindeki [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) öğesi. Yapılandırma sistemi döndürür bir <xref:System.Collections.IDictionary> nesne çağırdığınızda <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki örnekte adlı özel bir öğe bildirir  **\<sampleSection >** tarafından okunur ayarları içeren <xref:System.Configuration.SingleTagSectionHandler> sınıfı:

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

Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
