---
title: "&lt;kaldırma&gt; öğesi için &lt;configSections&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bf2cb49fbeb01ad176a1d24d711cebc97ba14004
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="remove-element-for-configsections"></a>\<kaldırma > öğesi için \<configSections >

Önceden tanımlanmış bölüm veya bölüm grubu kaldırır.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<kaldırma >**

## <a name="syntax"></a>Sözdizimi

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **adı**  | Gerekli öznitelik.<br><br>Bölüm veya kaldırmak için bölüm grubu adını belirtir. |

## <a name="parent-element"></a>Üst öğesi

|     | Açıklama |
| --- | ----------- |
| [**\<configSections >** öğesi](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimlerini içerir. |

# <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

Kullanabileceğiniz  **\<kaldırma >** öğesi yapılandırma dosyası hiyerarşisinde daha yüksek bir düzeyde tanımlanan uygulamanızı bölümler ve bölüm grupları kaldırın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte nasıl kullanılacağını gösterir  **\<kaldırma >** makine yapılandırma dosyasında önceden tanımlanmış bir bölümü kaldırmak için bir uygulama yapılandırma dosyasında öğesi.

Bölümü aşağıdaki makine yapılandırma dosyası kodu bildirir  **\<sampleSection >**:

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

Aşağıdaki uygulama yapılandırma dosyası kodu kaldırır  **\<sampleSection >** bölümü. Kaldırıldıktan sonra uygulama ayarlarında alınamıyor  **\<sampleSection >**.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
