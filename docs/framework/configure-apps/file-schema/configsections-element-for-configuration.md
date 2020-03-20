---
title: <configuration> için <configSections> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155355"
---
# <a name="configsections-element-for-configuration"></a>\<yapılandırma> için \<configSections> elemanı

Yapılandırma bölümü ve ad alanı bildirimleri içerir.

yapılandırma &nbsp; &nbsp;>[** \<**](configuration-element.md) **configSections \<>**

## <a name="attributes"></a>Öznitelikler

None

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<yapılandırma>**](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<bölüm>**](section-element.md) | Yapılandırma bölümü bildirimi içerir. |
| [**\<bölümGrup>**](sectiongroup-element-for-configsections.md) | Yapılandırma bölümleri için bir ad alanı tanımlar. |
| [**\<>kaldırmak**](remove-element-for-configsections.md) | Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır. |
| [**\<açık>**](clear-element-for-configsections.md) | Önceden tanımlanmış tüm bölümleri ve bölüm gruplarını temizler. |

## <a name="remarks"></a>Açıklamalar

Bu öğe bir yapılandırma dosyasındaysa, ** \<yapılandırma>** öğesinin ilk alt öğesi olmalıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, yapılandırma bölümünün nasıl tanımlanılıgı ve bu bölümün ayarlarını nasıl tanımlanabilirsiniz:

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

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
