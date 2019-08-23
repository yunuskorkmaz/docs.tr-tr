---
title: NameValueSectionHandler ve DictionarySectionHandler için özel öğe
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 890269857aaa00ce62195ccb2f4cb184b363b61e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921031"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>NameValueSectionHandler ve DictionarySectionHandler için özel öğe

<xref:System.Configuration.NameValueSectionHandler> Ve<xref:System.Configuration.DictionarySectionHandler> sınıflarını kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar.

[ **\<Yapılandırma >** ](configuration-element.md)\
&nbsp;&nbsp; **\<sectionName >**

## <a name="attributes"></a>Öznitelikler

Yok.

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<Yapılandırma >** ](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| ve için<xref:System.Configuration.NameValueSectionHandler> > ekleyin [ **\<** ](add-element-for-custom-2.md)<xref:System.Configuration.DictionarySectionHandler>  | Özel uygulama ayarları ekler. |
| ve için<xref:System.Configuration.NameValueSectionHandler> > Kaldır [ **\<** ](remove-element-for-custom-2.md)<xref:System.Configuration.DictionarySectionHandler> | Daha önce tanımlanmış bir ayarı kaldırır. |
| ve için<xref:System.Configuration.NameValueSectionHandler> > Temizle [ **\<** ](clear-element-for-custom-2.md)<xref:System.Configuration.DictionarySectionHandler> | Bir bölümdeki önceden tanımlanmış tüm ayarları temizler. |

## <a name="remarks"></a>Açıklamalar

**
          \<SectionName>** öğedir tarafından tanımlanan özel bir öğe bir **\<bölüm>** içindeki **\<configSections>** öğesi.

Aşağıdaki tabloda, ConfigurationSettings. GetConfig yönteminin her bir yapılandırma bölümü işleyicisi için döndürdüğü nesne türü gösterilmektedir:

| Yapılandırma bölümü işleyicisi                        | Dönüş türü                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.Configuration.DictionarySectionHandler> ve <xref:System.Configuration.NameValueSectionHandler> sınıflarını kullanan bölümlerin nasıl bildirilemeyeceğini gösterir.

İlk özel öğe <xref:System.Configuration.DictionarySectionHandler>  **\<** , `System.dll` derlemedeki sınıf tarafından okunan ayarları içeren dictionarysample >. İkinci özel öğe <xref:System.Configuration.NameValueSectionHandler> `System.dll`  **\<** , derleme içindeki sınıf tarafından okunan ayarları içeren MySection >.

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
