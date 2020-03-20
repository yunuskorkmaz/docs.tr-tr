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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154536"
---
# <a name="remove-element-for-configsections"></a>\<configSections \<> için> öğeyi kaldırmak

Önceden tanımlanmış bir bölümü veya bölüm grubunu kaldırır.

[**\<yapılandırma>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configBölüm>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>kaldırmak**

## <a name="syntax"></a>Sözdizimi

```xml
<remove name="section name or section group name" />
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

Yapılandırma dosyası ** \<** hiyerarşisinde daha yüksek bir düzeyde tanımlanan bölümleri ve bölüm gruplarını uygulamanızdan kaldırmak için kaldır>öğesini kullanabilirsiniz.

## <a name="example"></a>Örnek

Aşağıdaki örnek, makine yapılandırma dosyasında daha önce tanımlanmış bir bölümü kaldırmak için uygulama yapılandırma dosyasındaki ** \<kaldırma>** öğesini nasıl kullanacağımı gösterir.

Aşağıdaki makine yapılandırma dosya kodu bölüm ** \<örnekBölüm>** bildirir:

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

Aşağıdaki uygulama yapılandırma dosya kodu ** \<örnekBölüm>** bölümünü kaldırır. Kaldırıldıktan sonra, uygulama ** \<örnekBölüm>'ndaki **ayarları alamıyor.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
