---
title: <configuration> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d522d004630dee942e24c39a936feae7dc957bd5
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300786"
---
# <a name="configsections-element-for-configuration"></a>\<configSections > öğesi için \<yapılandırma >

Yapılandırma bölümü ve ad alanı bildirimi içerir.

[ **\<Yapılandırma >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp; **\<configSections >**

## <a name="attributes"></a>Öznitelikler

Yok.

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<Yapılandırma >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [ **\<Bölüm >** ](~/docs/framework/configure-apps/file-schema/section-element.md) | Bir yapılandırma bölümü bildirimi içerir. |
| [ **\<sectionGroup >** ](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Yapılandırma bölümleri için bir ad alanı tanımlar. |
| [ **\<kaldırma >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | Önceden tanımlanmış bir bölüm veya bölüm grubu kaldırır. |
| [ **\<Temizleme >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler. |

## <a name="remarks"></a>Açıklamalar

Bu öğe bir yapılandırma dosyasında, ilk alt öğesi olmalıdır  **\<yapılandırma >** öğesi.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma bölümü tanımlayın ve bu bölümün ayarlarını tanımlamak gösterilmektedir:

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
