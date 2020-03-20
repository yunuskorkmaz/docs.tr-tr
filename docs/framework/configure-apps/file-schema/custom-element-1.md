---
title: SingleTagSectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 04360a796b18cf1e414f1f84bff247a1e9d8ef9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155160"
---
# <a name="custom-element-for-singletagsectionhandler"></a>SingleTagSectionHandler için özel öğe

Bir bölüm> öğesi tarafından tanımlanan ve \< <xref:System.Configuration.SingleTagSectionHandler> sınıfı kullanan özel bir yapılandırma bölümündeki ayarları tanımlar.

yapılandırma &nbsp; &nbsp;>[** \<**](configuration-element.md) * \<bölümName>*

## <a name="syntax"></a>Sözdizimi

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Öznitelikler

Öznitelikler ve öznitelik değerleri kullanıcı tanımlanır.

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<yapılandırma>**](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

None

## <a name="remarks"></a>Açıklamalar

sectionName>[** \<öğesi, configSections>**](configsections-element-for-configuration.md) öğesindeki bir [** \<bölüm>**](section-element.md) etiketiyle tanımlanan özel bir öğedir. ** \<** Yapılandırma sistemi, <xref:System.Collections.IDictionary> <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Configuration.SingleTagSectionHandler> sınıf tarafından okunan ayarları içeren ** \<örnekBölüm>** adlı özel bir öğe bildirir:

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
