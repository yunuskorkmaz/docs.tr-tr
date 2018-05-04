---
title: '&lt;configSections&gt; öğesi için &lt;yapılandırma&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 33406a67389cdf857fa5030e20d8a4dec7662741
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="configsections-element-for-configuration"></a>\<configSections > öğesi için \<yapılandırma >

Yapılandırma bölümü ve ad alanı bildirimlerini içerir.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<configSections >**

## <a name="attributes"></a>Öznitelikler

Yok.

## <a name="parent-element"></a>Üst öğesi

|     | Açıklama |
| --- | ----------- |
| [**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<Bölüm >**](~/docs/framework/configure-apps/file-schema/section-element.md) | Bir yapılandırma bölümü bildirimi içerir. |
| [**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Yapılandırma bölümleri için bir ad alanını tanımlar. |
| [**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | Önceden tanımlanmış bölüm veya bölüm grubu kaldırır. |
| [**\<Clear >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler. |

## <a name="remarks"></a>Açıklamalar

Bu öğe bir yapılandırma dosyası ise, ilk alt öğesi olmalıdır  **\<configuration >** öğesi.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma bölümü ve o bölümün ayarlarının tanımlamaya gösterilmektedir:

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
