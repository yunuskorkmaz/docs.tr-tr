---
title: <configSections> için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154536"
---
# <a name="remove-element-for-configsections"></a>\<configSections> için \<remove> öğesi

Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

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
| [**\<configSections>** Dosyalarında](configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimleri içerir. |

## <a name="child-elements"></a>Alt öğeleri

Yok

## <a name="remarks"></a>Açıklamalar

**\<remove>** Uygulamanızı yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan bölümleri ve bölüm gruplarını kaldırmak için öğesini kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, **\<remove>** daha önce makine yapılandırma dosyasında tanımlanan bir bölümü kaldırmak için bir uygulama yapılandırma dosyasında öğesinin nasıl kullanılacağını gösterir.

Aşağıdaki makine yapılandırma dosyası kodu şu bölümü bildirir **\<sampleSection>** :

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

Aşağıdaki uygulama yapılandırma dosyası kodu **\<sampleSection>** bölümünü kaldırır. Kaldırma işleminden sonra uygulama, içindeki ayarları alamaz **\<sampleSection>** .

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
