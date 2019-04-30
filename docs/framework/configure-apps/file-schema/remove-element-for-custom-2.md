---
title: <remove> NameValueSectionHandler ve DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: guardrex
ms.author: mairaw
ms.openlocfilehash: c86d231a4e3e8e15df94017a6ca461b365643ea5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705109"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<kaldırma > NameValueSectionHandler ve DictionarySectionHandler

Önceden tanımlanmış ayar kaldırır.

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
| **anahtar**   | Gerekli öznitelik.<br><br>Kaldırmak için ayar adını belirtir. |

## <a name="parent-element"></a>Üst öğe

| Öğe | Açıklama |
| ------- | ------------|
| [**\<sectionName >** öğesi](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Ayarları kullanan özel yapılandırma bölümleri tanımlar <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıfları. |

## <a name="child-elements"></a>Alt öğeleri

None

## <a name="remarks"></a>Açıklamalar

Kullanabileceğiniz  **\<kaldırma >** uygulamanızdan yapılandırma dosyası hiyerarşisindeki daha yüksek düzeyde tanımlanan ayarları kaldırmak için öğesi.

## <a name="example"></a>Örnek

Aşağıdaki örnek nasıl kullanılacağını gösterir  **\<kaldırma >** makine yapılandırma dosyasında önceden tanımlanmış ayarları kaldırmak için bir uygulama yapılandırma dosyasında öğesi.

Aşağıdaki makine yapılandırma dosyası kod bölümü bildirir  **\<mySection >** ve iki ayarı ekler `key1` ve `key2`, ona:

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

Aşağıdaki uygulama yapılandırma dosyası kodu kaldırır `key2` ayarını  **\<mySection >**:

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
