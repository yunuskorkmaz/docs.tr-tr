---
title: NameValueSectionHandler ve DictionarySectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215490"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler ve DictionarySectionHandler için özel öğe

Ve sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> .

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a>Öznitelikler

Yok

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<add>**](add-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler>ve için<xref:System.Configuration.DictionarySectionHandler>  | Özel uygulama ayarları ekler. |
| [**\<remove>**](remove-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler>ve için<xref:System.Configuration.DictionarySectionHandler> | Daha önce tanımlanmış bir ayarı kaldırır. |
| [**\<clear>**](clear-element-for-custom-2.md)<xref:System.Configuration.NameValueSectionHandler>ve için<xref:System.Configuration.DictionarySectionHandler> | Bir bölümdeki önceden tanımlanmış tüm ayarları temizler. |

## <a name="remarks"></a>Açıklamalar

**\<sectionName>** Öğesi, öğesinde bir etiketi tarafından tanımlanan özel bir öğedir **\<section>** **\<configSections>** .

Aşağıdaki tabloda, ConfigurationSettings. GetConfig yönteminin her bir yapılandırma bölümü işleyicisi için döndürdüğü nesne türü gösterilmektedir:

| Yapılandırma bölümü işleyicisi                        | Dönüş türü                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Örnek

Aşağıdaki örnek, ve sınıflarını kullanan bölümlerin nasıl bildirilemeyeceğini gösterir <xref:System.Configuration.DictionarySectionHandler> <xref:System.Configuration.NameValueSectionHandler> .

İlk özel öğe, **\<dictionarySample>** derleme içindeki sınıf tarafından okunan ayarları içerir <xref:System.Configuration.DictionarySectionHandler> `System.dll` . İkinci özel öğe, **\<mySection>** derleme içindeki sınıf tarafından okunan ayarları içerir <xref:System.Configuration.NameValueSectionHandler> `System.dll` .

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
