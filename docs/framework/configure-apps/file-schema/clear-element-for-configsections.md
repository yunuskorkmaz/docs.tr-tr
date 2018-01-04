---
title: "&lt;Clear&gt; öğesi için &lt;configSections&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e48887cf7e227f463b92edd50f69746bbd8abd0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clear-element-for-configsections"></a>\<Clear > öğesi için \<configSections >

Tüm önceden tanımlanmış bölümler ve bölüm grupları temizler.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Clear >**

## <a name="syntax"></a>Sözdizimi

```xml
<clear/>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **adı**  | Gerekli öznitelik.<br><br>Bölüm veya kaldırmak için bölüm grubu adını belirtir. |

## <a name="parent-element"></a>Üst öğesi

|     | Açıklama |
| --- | ----------- |
| [**\<configSections >** öğesi](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimlerini içerir. |

# <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

 **\<Temizleyin >** uygulamanızdan geçerli yapılandırma dosyası veya yapılandırma dosyası hiyerarşisinde daha yüksek düzeyde daha önce tanımlanan öğeyi kaldırır tüm bölümler ve bölüm grupları.

## <a name="example"></a>Örnek

Bu örnek bir uygulama yapılandırma dosyasını ve makine yapılandırma dosyasını tanımlar ve nasıl kullanılacağını gösterir  **\<temizleyin >** önceden tanımlanmış bir bölümü temizlemek için bir uygulama yapılandırma dosyasında öğesi makine yapılandırma dosyası.

İki bölüm, aşağıdaki makine yapılandırma dosyası kodu bildirir  **\<sampleSection >** ve  **\<anotherSampleSection >**, önce uygulamayı okuyun, yapılandırma dosyası:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

Aşağıdaki uygulama yapılandırma dosyası kodu daha önce bildirilen tüm bölümleri temizler. Uygulama kullanın veya makine yapılandırma dosyasında bildirilen bölümlerden birine ayarlarında alın. Ancak, ayarlarından kullanabilirsiniz  **\<anotherSection >** sonra geldiğinden  **\<temizleyin >** öğesi.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
