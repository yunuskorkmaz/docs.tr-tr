---
title: NameValueSectionHandler ve DictionarySectionHandler için <add> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215433"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler ve DictionarySectionHandler için > öğesi \<ekleyin

Özel uygulama ayarları ekler. Her **\<add >** etiketi bir anahtar/değer çifti içerir.

[ **\<yapılandırma >** ](configuration-element.md)\
&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<ekleme >**

## <a name="syntax"></a>Sözdizimi

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Öznitelikler

| Öznitelik | Açıklama |
| --------- | ----------- |
| **anahtar**   | Gerekli öznitelik.<br><br>Ayarın adını belirtir. |
| **value** | Gerekli öznitelik.<br><br>Ayarın değerini belirtir. |

## <a name="parent-element"></a>Üst öğe

| Öğe | Açıklama |
| ------- | ------------|
| [ **\<sectionName >** Dosyalarında](custom-element-2.md) | <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar. |

## <a name="child-elements"></a>Alt öğeleri

Hiçbiri

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir özel yapılandırma bölümünün nasıl tanımlanacağını gösterir ve **\<add >** öğesini kullanarak ayarları bölümüne yerleştirir:

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

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
