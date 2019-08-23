---
title: SingleTagSectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8fae3673fe72d036802cb1a8366aaa2430c38884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927497"
---
# <a name="custom-element-for-singletagsectionhandler"></a>SingleTagSectionHandler için özel öğe

Bir \<Bölüm > öğesi tarafından tanımlanan ve <xref:System.Configuration.SingleTagSectionHandler> sınıfını kullanan özel bir yapılandırma bölümünde ayarları tanımlar.

[ **\<Yapılandırma >** ](configuration-element.md)   
&nbsp;&nbsp; *\<sectionName >*

## <a name="syntax"></a>Sözdizimi

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Öznitelikler

Öznitelikler ve öznitelik değerleri Kullanıcı tanımlı ' dır.

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<Yapılandırma >** ](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

SectionName > öğesi, [**configSections \<>** ](configsections-element-for-configuration.md) öğesinde bir [ **\<Bölüm >** ](section-element.md) etiketi tarafından tanımlanan özel bir öğedir.  **\<** Yapılandırma sistemi, çağırdığınızda <xref:System.Collections.IDictionary> <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>bir nesne döndürür.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Configuration.SingleTagSectionHandler> sınıf tarafından okunan ayarları içeren  **\<sampleSection >** adlı özel bir öğe bildirir:

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
