---
title: <configuration> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927666"
---
# <a name="configsections-element-for-configuration"></a>\<> yapılandırma için \<configSections > öğesi

Yapılandırma bölümü ve ad alanı bildirimleri içerir.

[ **\<Yapılandırma >** ](configuration-element.md)   
&nbsp;&nbsp; **\<configSections >**

## <a name="attributes"></a>Öznitelikler

Yok.

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<Yapılandırma >** ](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [ **\<Bölüm >** ](section-element.md) | Bir yapılandırma bölümü bildirimi içerir. |
| [ **\<sectionGroup >** ](sectiongroup-element-for-configsections.md) | Yapılandırma bölümleri için bir ad alanı tanımlar. |
| [ **\<> Kaldır**](remove-element-for-configsections.md) | Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır. |
| [ **\<> Temizle**](clear-element-for-configsections.md) | Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler. |

## <a name="remarks"></a>Açıklamalar

Bu öğe bir yapılandırma dosyasında ise,  **\<Yapılandırma >** öğesinin ilk alt öğesi olmalıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma bölümünün nasıl tanımlanacağını ve bu bölüm için ayarların nasıl tanımlanacağını göstermektedir:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
