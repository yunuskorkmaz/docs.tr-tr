---
title: <configSections> için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 4ff9bb537a31e28dbd4b878c1bc04c96262f85ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927464"
---
# <a name="remove-element-for-configsections"></a>\<configSections için \<> öğesi > Kaldır

Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.

[ **\<Yapılandırma >** ](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<> Kaldır**

## <a name="syntax"></a>Sözdizimi

```xml
<remove name="section name or section group name" />
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

Yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanmış olan uygulamalarınızdan bölümleri ve bölüm gruplarını kaldırmak için  **\<Remove >** öğesini kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, daha önce makine yapılandırma dosyasında tanımlanan bir bölümü kaldırmak için bir uygulama yapılandırma dosyasında  **\<Remove >** öğesinin nasıl kullanılacağını gösterir.

Aşağıdaki makine yapılandırma dosyası kodu,  **\<sampleSection >** bölümünü bildirir:

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

Aşağıdaki uygulama yapılandırma dosyası kodu,  **\<sampleSection >** bölümünü kaldırır. Kaldırma işleminden sonra uygulama  **\<sampleSection >** ayarlarını alamaz.

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
