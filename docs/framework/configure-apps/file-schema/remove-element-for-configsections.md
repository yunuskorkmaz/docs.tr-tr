---
title: <configSections> için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efc7208aa51cbf6abdb2fe151d48071c0aa95b5c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089046"
---
# <a name="remove-element-for-configsections"></a>\<configSections için > öğesini \<kaldırın >

Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.

[ **\<configuration >** ](configuration-element.md) \
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<kaldır >**

## <a name="syntax"></a>Sözdizimi

```xml
<remove name="section name or section group name" />
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

Yok.

## <a name="remarks"></a>Açıklamalar

Uygulamanızın yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış bölümleri ve bölüm gruplarını kaldırmak için **\<remove >** öğesini kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, daha önce makine yapılandırma dosyasında tanımlanan bir bölümü kaldırmak üzere bir uygulama yapılandırma dosyasında **\<remove >** öğesinin nasıl kullanılacağını gösterir.

Aşağıdaki makine yapılandırma dosyası kodu, **\<samplesection >** bölümünü bildirir:

```xml
<!-- Machine.config file -->
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

Aşağıdaki uygulama yapılandırma dosyası kodu **\<samplesection >** bölümünü kaldırır. Kaldırma işleminden sonra uygulama, **\<sampleSection**içindeki ayarları alamaz.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
