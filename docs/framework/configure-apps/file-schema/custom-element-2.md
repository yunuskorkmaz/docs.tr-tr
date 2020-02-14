---
title: NameValueSectionHandler ve DictionarySectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215490"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler ve DictionarySectionHandler için özel öğe

<xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar.

[ **\<yapılandırma >** ](configuration-element.md)\
&nbsp;&nbsp; **\<sectionName >**

## <a name="attributes"></a>Öznitelikler

Hiçbiri

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<Yapılandırma >** ](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> için [ **>\<ekleyin**](add-element-for-custom-2.md)  | Özel uygulama ayarları ekler. |
| <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> için [ **>\<kaldırın**](remove-element-for-custom-2.md) | Daha önce tanımlanmış bir ayarı kaldırır. |
| <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> için [ **\<> Temizle**](clear-element-for-custom-2.md) | Bir bölümdeki önceden tanımlanmış tüm ayarları temizler. |

## <a name="remarks"></a>Açıklamalar

**\<SectionName>** öğedir tarafından tanımlanan özel bir öğe bir **\<bölüm>** içindeki **\<configSections>** öğesi.

Aşağıdaki tabloda, ConfigurationSettings. GetConfig yönteminin her bir yapılandırma bölümü işleyicisi için döndürdüğü nesne türü gösterilmektedir:

| Yapılandırma bölümü işleyicisi                        | Dönüş türü                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Configuration.DictionarySectionHandler> ve <xref:System.Configuration.NameValueSectionHandler> sınıfları kullanan bölümlerin nasıl bildirilemeyeceğini gösterir.

İlk özel öğe, `System.dll` derlemesinde <xref:System.Configuration.DictionarySectionHandler> sınıfı tarafından okunan ayarları içeren **\<dictionarySample >** . İkinci özel öğe, `System.dll` derlemesinde <xref:System.Configuration.NameValueSectionHandler> sınıfı tarafından okunan ayarları içeren **mySection >\<** .

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
