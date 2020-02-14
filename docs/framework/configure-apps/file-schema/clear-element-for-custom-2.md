---
title: NameValueSectionHandler ve DictionarySectionHandler için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: f6d860f35d22002030ffa3d09dd0d8a96116bf5e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214752"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler ve DictionarySectionHandler için \<Clear > öğesi

Bir bölümdeki önceden tanımlanmış tüm ayarları temizler.

[ **\<yapılandırma >** ](configuration-element.md)\
&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<temizle >**

## <a name="syntax"></a>Sözdizimi

```xml
<clear />
```

## <a name="attributes"></a>Öznitelikler

Hiçbiri

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ------------|
| [ **\<sectionName >** Dosyalarında](custom-element-2.md) | <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar. |

## <a name="child-elements"></a>Alt öğeleri

Hiçbiri

## <a name="remarks"></a>Açıklamalar

Uygulamanızın yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış tüm ayarları kaldırmak için **\<clear >** öğesini kullanabilirsiniz.

## <a name="example"></a>Örnek

Bu örnek bir makine yapılandırma dosyası ve bir uygulama yapılandırma dosyası tanımlar ve daha önce makine yapılandırma dosyasında tanımlanan bölümleri temizlemek için bir uygulama yapılandırma dosyasında **\<clear >** öğesinin nasıl kullanılacağını gösterir.

Aşağıdaki makine yapılandırma dosyası kodu, **\<mysection >** bölümünü bildirir:

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

Aşağıdaki uygulama yapılandırma dosyası kodu, tüm ayarları **\<mySection >** kaldırır. Uygulama, makine yapılandırma dosyasının **\<mySection >** bölümünde belirtilen ayarlardan hiçbirini alamıyor.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
