---
title: '&lt;kaldırma&gt; NameValueSectionHandler ve DictionarySectionHandler öğesi'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 61f1c98d3f12b5aa1d25595ca28328602683b073
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<kaldırma > öğesi NameValueSectionHandler ve DictionarySectionHandler için

Önceden tanımlanmış bir ayar kaldırır.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<kaldırma >**

## <a name="syntax"></a>Sözdizimi

```xml
<add remove="key" />
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **Anahtarı**   | Gerekli öznitelik.<br><br>Kaldırmak için ayarının adını belirtir. |

## <a name="parent-element"></a>Üst öğesi

| Öğe | Açıklama |
| ------- | ------------|
| [**\<sectionName >** öğesi](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıfları. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

Kullanabileceğiniz  **\<kaldırma >** öğesi yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanan uygulamanızın ayarlarını kaldırın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<kaldırma >** makine yapılandırma dosyasında önceden tanımlanmış ayarları kaldırmak için bir uygulama yapılandırma dosyasında öğesi.

Bölümü aşağıdaki makine yapılandırma dosyası kodu bildirir  **\<mySection >** ve iki ayarları ekler `key1` ve `key2`, ona:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Aşağıdaki uygulama yapılandırma dosyası kodu kaldırır `key2` setting from  **\<mySection >**:

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
