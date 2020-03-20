---
title: <configSections> için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155433"
---
# <a name="clear-element-for-configsections"></a>\<configSections \<> için net> eleman

Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler.

&nbsp; &nbsp; &nbsp; &nbsp; ** \<** [** \<konsinyon**](configsections-element-for-configuration.md)>&nbsp; &nbsp;yapılandırmaBölümleri>açık>[** \<**](configuration-element.md)

## <a name="syntax"></a>Sözdizimi

```xml
<clear/>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **Adı**  | Gerekli öznitelik.<br><br>Kaldırılacak bölüm veya bölüm grubunun adını belirtir. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [** \<configSections>** Öğe](configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimleri içerir. |

## <a name="child-elements"></a>Alt öğeleri

None

## <a name="remarks"></a>Açıklamalar

** \<Açık>** öğesi, geçerli yapılandırma dosyasında veya yapılandırma dosyası hiyerarşisinde daha önce tanımlanan tüm bölümleri ve bölüm gruplarını uygulamanızdan kaldırır.

## <a name="example"></a>Örnek

Bu örnek, bir makine yapılandırma dosyası ve bir uygulama yapılandırma dosyası tanımlar ve makine yapılandırma dosyasında daha önce tanımlanan bölümleri temizlemek için bir uygulama yapılandırma dosyasındaki ** \<açık>** öğesinin nasıl kullanılacağını gösterir.

Aşağıdaki makine yapılandırma dosya kodu iki bölüm bildirir, ** \<örnekBölüm>** ve ** \<başka ÖrnekBölüm>**, hangi uygulama yapılandırma dosyası önce okunur:

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

Aşağıdaki uygulama yapılandırma dosya kodu, daha önce bildirilen tüm bölümleri temizler. Uygulama, makine yapılandırma dosyasında bildirilen bölümlerin herhangi birinde ayarları kullanamaz veya alamaz. Ancak, ** \<net>** öğesi sonra gelir, çünkü ** \<başka bir Bölüm>** ayarları kullanabilirsiniz.

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

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
