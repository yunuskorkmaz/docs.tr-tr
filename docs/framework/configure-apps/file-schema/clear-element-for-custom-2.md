---
title: <clear> NameValueSectionHandler ve DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ad3ac93b2a7f92cd33787620fc0caa2b632aa072
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281885"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Temizle > NameValueSectionHandler ve DictionarySectionHandler

Bir bölümdeki tüm önceden tanımlanmış ayarlar temizler.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Temizleme >**

## <a name="syntax"></a>Sözdizimi

```xml
<clear />
```

## <a name="attributes"></a>Öznitelikler

Hiçbiri

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ------------|
| [**\<sectionName >** öğesi](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Ayarları kullanan özel yapılandırma bölümleri tanımlar <xref:System.Configuration.NameValueSectionHandler> ve <xref:System.Configuration.DictionarySectionHandler> sınıfları. |

## <a name="child-elements"></a>Alt öğeleri

Hiçbiri

## <a name="remarks"></a>Açıklamalar

Kullanabileceğiniz  **\<Temizle >** uygulamanızdan yapılandırma dosyası hiyerarşisindeki daha yüksek bir düzeyinde tanımlanan tüm ayarları kaldırmak için öğesi.

## <a name="example"></a>Örnek

Bu örnek nasıl kullanılacağını gösterir ve makine yapılandırma dosyası ve bir uygulama yapılandırma dosyasını tanımlar  **\<Temizle >** önceden tanımlanmış bir bölümü temizlemek için bir uygulama yapılandırma dosyasında öğesi makine yapılandırma dosyası.

Aşağıdaki makine yapılandırma dosyası kod bölümü bildirir  **\<mySection >**:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Aşağıdaki uygulama yapılandırma dosyası kodu, tüm ayarlarını kaldırır  **\<mySection >**. Uygulama içinde bildirilen ayarlardan herhangi birini alınamıyor,  **\<mySection >** makine yapılandırma dosyası bölümünü.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
