---
title: "Özel öğe NameValueSectionHandler ve DictionarySectionHandler"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2154e2a178050e5bafa7d19f37a766141d0a5838
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Özel öğe NameValueSectionHandler ve DictionarySectionHandler

Kullanan özel yapılandırma bölümlerinin ayarlarını tanımlar <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıfları.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<sectionName >**

## <a name="attributes"></a>Öznitelikler

Yok.

## <a name="parent-element"></a>Üst öğesi

|     | Açıklama |
| --- | ----------- |
| [**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<Ekle >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) için <xref:System.Configuration.NameValueSectionHandler> ve<xref:System.Configuration.DictionarySectionHandler>  | Özel uygulama ayarlarını ekler. |
| [**\<kaldırma >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) için <xref:System.Configuration.NameValueSectionHandler> ve<xref:System.Configuration.DictionarySectionHandler> |    Önceden tanımlanmış bir ayar kaldırır. |
| [**\<Clear >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) için <xref:System.Configuration.NameValueSectionHandler> ve<xref:System.Configuration.DictionarySectionHandler> | Bir bölümdeki tüm önceden tanımlanmış ayarları temizler. |

## <a name="remarks"></a>Açıklamalar

 **\<SectionName >** öğesidir tarafından tanımlanan bir özel bir  **\<bölüm >** içinde etiketi  **\<configSections >**öğesi.

Aşağıdaki tabloda, her yapılandırma bölümü işleyicisi için nesne ConfigurationSettings.GetConfig yöntemi türünü döndürür gösterilmektedir:

| Yapılandırma bölümü işleyicisi                        | Dönüş türü                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Örnek

Aşağıdaki örnek kullanan bölümler bildirmek nasıl gösterir <xref:System.Configuration.DictionarySectionHandler> ve <xref:System.Configuration.NameValueSectionHandler> sınıfları. 

İlk özel öğe  **\<dictionarySample >**, tarafından okunur ayarları içeren <xref:System.Configuration.DictionarySectionHandler> sınıfını `System.dll` derleme. İkinci özel öğesi  **\<mySection >**, tarafından okunur ayarları içeren <xref:System.Configuration.NameValueSectionHandler> sınıfını `System.dll` derleme.

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

Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
