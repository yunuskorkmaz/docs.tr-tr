---
description: 'Hakkında daha fazla bilgi edinin: <add> NameValueSectionHandler ve DictionarySectionHandler için öğesi'
title: <add> NameValueSectionHandler ve DictionarySectionHandler için öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 5a8cf22b21370e60086408f792f8137386d07aa3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713058"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<add> NameValueSectionHandler ve DictionarySectionHandler için öğesi

Özel uygulama ayarları ekler. Her **\<add>** etiket bir anahtar/değer çifti içerir.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>Syntax

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Öznitelikler

| Öznitelik | Açıklama |
| --------- | ----------- |
| **anahtar**   | Gerekli öznitelik.<br><br>Ayarın adını belirtir. |
| **değer** | Gerekli öznitelik.<br><br>Ayarın değerini belirtir. |

## <a name="parent-element"></a>Üst öğe

| Öğe | Açıklama |
| ------- | ------------|
| [**\<sectionName>** Dosyalarında](custom-element-2.md) | Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> . |

## <a name="child-elements"></a>Alt öğeleri

Hiçbiri

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir özel yapılandırma bölümünün nasıl tanımlanacağını ve bu **\<add>** öğenin, ayarları bölümüne koymak için nasıl kullanılacağını gösterir:

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
