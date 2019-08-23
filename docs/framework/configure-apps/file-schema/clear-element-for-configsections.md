---
title: <configSections> için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c06fca8b83638fb47bedb21863cb9b200cd211f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927738"
---
# <a name="clear-element-for-configsections"></a>\<configSections için \<> öğesi > Temizle

Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.

[ **\<Yapılandırma >** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<> Temizle**

## <a name="syntax"></a>Sözdizimi

```xml
<clear/>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **name**  | Gerekli öznitelik.<br><br>Kaldırılacak bölüm veya bölüm grubunun adını belirtir. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **configSections>\<** öğesi](configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimleri içerir. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

**\<Clear >** öğesi, geçerli yapılandırma dosyasında daha önce tanımlanan veya yapılandırma dosyası hiyerarşisindeki daha yüksek bir düzeyde bulunan uygulamanızdaki tüm bölümleri ve bölüm gruplarını kaldırır.

## <a name="example"></a>Örnek

Bu örnek bir makine yapılandırma dosyası ve bir uygulama yapılandırma dosyası tanımlar ve daha önce makine yapılandırmasında tanımlanmış bölümleri temizlemek için bir uygulama yapılandırma dosyasında  **\<Clear >** öğesinin nasıl kullanılacağını gösterir dosyasýný.

Aşağıdaki makine yapılandırma dosyası kodu, uygulama yapılandırma dosyasından önce okunan  **\<sampleSection >** ve  **\<anotherSampleSection >** olmak üzere iki bölüm bildirir:

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

Aşağıdaki uygulama yapılandırma dosyası kodu, önceden tanımlanmış tüm bölümleri temizler. Uygulama, makine yapılandırma dosyasında belirtilen bölümlerden birindeki ayarları kullanamaz veya alamaz. Ancak **, \<Clear >** öğesinden sonra geldiğinden, bu  **\<>, anotherSection** içindeki ayarları kullanabilir.

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
