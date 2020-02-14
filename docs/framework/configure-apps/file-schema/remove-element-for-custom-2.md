---
title: NameValueSectionHandler ve DictionarySectionHandler için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214762"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler ve DictionarySectionHandler için > öğesini \<kaldırın

Daha önce tanımlanmış bir ayarı kaldırır.

[ **\<yapılandırma >** ](configuration-element.md)\
&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<kaldır >**

## <a name="syntax"></a>Sözdizimi

```xml
<add remove="key" />
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **anahtar**   | Gerekli öznitelik.<br><br>Kaldırılacak ayarın adını belirtir. |

## <a name="parent-element"></a>Üst öğe

| Öğe | Açıklama |
| ------- | ------------|
| [ **\<sectionName >** Dosyalarında](custom-element-2.md) | <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar. |

## <a name="child-elements"></a>Alt öğeleri

Hiçbiri

## <a name="remarks"></a>Açıklamalar

Uygulamanızın yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış ayarları kaldırmak için **\<remove >** öğesini kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, daha önce makine yapılandırma dosyasında tanımlanan ayarları kaldırmak için bir uygulama yapılandırma dosyasında **\<remove >** öğesinin nasıl kullanılacağını gösterir.

Aşağıdaki makine yapılandırma dosyası kodu, **\<mysection >** bölümünü bildirir ve `key1` ve `key2`iki ayarı ekler:

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

Aşağıdaki uygulama yapılandırma dosyası kodu, `key2` ayarı **\<mySection >** kaldırır:

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
