---
description: 'Daha fazla bilgi edinin: SingleTagSectionHandler için özel öğe'
title: SingleTagSectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 83022a1ebf295b89d5f868589e3d9a77c78e3fab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99729985"
---
# <a name="custom-element-for-singletagsectionhandler"></a>SingleTagSectionHandler için özel öğe

, Bir öğesi tarafından tanımlanan \<section> ve sınıfını kullanan özel bir yapılandırma bölümünde ayarları tanımlar <xref:System.Configuration.SingleTagSectionHandler> .

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*

## <a name="syntax"></a>Syntax

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a>Öznitelikler

Öznitelikler ve öznitelik değerleri Kullanıcı tanımlı ' dır.

## <a name="parent-element"></a>Üst öğe

|     | Description |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

Yok

## <a name="remarks"></a>Açıklamalar

**\<sectionName>** Öğesi, öğesinde bir etiketi tarafından tanımlanan özel bir öğedir [**\<section>**](section-element.md) [**\<configSections>**](configsections-element-for-configuration.md) . Yapılandırma sistemi, çağırdığınızda bir <xref:System.Collections.IDictionary> nesne döndürür <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> .

## <a name="example"></a>Örnek

Aşağıdaki örnek, **\<sampleSection>** sınıfı tarafından okunan ayarları içeren adlı özel bir öğe bildirir <xref:System.Configuration.SingleTagSectionHandler> :

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

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan dosyaları *Web.config* kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
