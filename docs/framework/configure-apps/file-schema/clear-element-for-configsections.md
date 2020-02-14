---
title: <clear> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: e8c9b0479bba839a74dff300f0766838b5d99c8d
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214831"
---
# <a name="clear-element-for-configsections"></a>\<configSections için > öğesini \<temizleyin >

Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.

[ **\<yapılandırma >** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<temizle >**

## <a name="syntax"></a>Sözdizimi

```xml
<clear/>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **ada**  | Gerekli öznitelik.<br><br>Kaldırılacak bölüm veya bölüm grubunun adını belirtir. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<configSections >** Dosyalarında](configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimleri içerir. |

## <a name="child-elements"></a>Alt öğeleri

Hiçbiri

## <a name="remarks"></a>Açıklamalar

**\<clear >** öğesi, geçerli yapılandırma dosyasında daha önce tanımlanan veya yapılandırma dosyası hiyerarşisindeki daha yüksek bir düzeyde bulunan uygulamanızdaki tüm bölümleri ve bölüm gruplarını kaldırır.

## <a name="example"></a>Örnek

Bu örnek bir makine yapılandırma dosyası ve bir uygulama yapılandırma dosyası tanımlar ve daha önce makine yapılandırma dosyasında tanımlanan bölümleri temizlemek için bir uygulama yapılandırma dosyasında **\<clear >** öğesinin nasıl kullanılacağını gösterir.

Aşağıdaki makine yapılandırma dosyası kodu, **\<samplesection >** ve **\<anothersamplesection >** uygulama yapılandırma dosyasından önce okunan iki bölüm bildirir:

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

Aşağıdaki uygulama yapılandırma dosyası kodu, önceden tanımlanmış tüm bölümleri temizler. Uygulama, makine yapılandırma dosyasında belirtilen bölümlerden birindeki ayarları kullanamaz veya alamaz. Ancak, **\<clear >** öğesinden sonra geldiği Için **\<anothersection >** ayarları kullanabilir.

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

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
