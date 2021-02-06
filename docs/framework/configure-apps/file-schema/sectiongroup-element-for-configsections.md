---
description: 'İçin: öğesi hakkında daha fazla bilgi <sectionGroup><configSections>'
title: <configSections> için <sectionGroup> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: 0d822b98acbc041b9d6e146e9cd15848a73d2f88
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639893"
---
# <a name="sectiongroup-element-for-configsections"></a>\<configSections> için \<sectionGroup> öğesi

Yapılandırma bölümleri için bir ad alanı tanımlar.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**

## <a name="syntax"></a>Syntax

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **ada**  | Gerekli öznitelik.<br><br>Tanımladığınız bölüm grubunun adını belirtir. |

## <a name="parent-element"></a>Üst öğe

|     | Description |
| --- | ----------- |
| [**\<configSections>** Dosyalarında](configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimleri içerir. |

## <a name="child-elements"></a>Alt öğeleri

|     | Description |
| --- | ----------- |
| [**\<section>**](section-element.md) | Bir yapılandırma bölümü bildirimi içerir. |

## <a name="remarks"></a>Açıklamalar

Bölüm grubunu bildirmek, yapılandırma bölümleri için bir kapsayıcı etiketi oluşturur ve başka biri tarafından tanımlanan yapılandırma bölümleriyle adlandırma çakışması olmamasını sağlar. Öğeleri birbirlerine iç içe yerleştirebilirsiniz **\<sectionGroup>** .

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir bölüm grubunun nasıl bildirilemeyeceğini ve bölüm grubu içinde bölümlerin nasıl bildirilemeyeceğini göstermektedir:

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
