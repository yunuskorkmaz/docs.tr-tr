---
title: '&lt;bölüm&gt; öğesi'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 17b44ca93efc26f4732f5fe2926f894257d8f984
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="section-element"></a>\<Bölüm > öğesi

Bir yapılandırma bölümü bildirimi içerir.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Bölüm >**

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<Bölüm >**

## <a name="syntax"></a>Sözdizimi

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Gerekli öznitelikler

|           | Açıklama |
| --------- | ----------- |
| **Adı**  | Yapılandırma bölümünün adını belirtir. |
| **Türü**  | Yapılandırma dosyasından bölüm okur yapılandırma bölümü işleyici sınıf adını belirtir. Tür değeri "fully-qualified-section-handler-class-name, basit derleme adı" sözdizimine sahip. Kök filename olmadan basit derleme adı: *.dll* dosya uzantısı. |

## <a name="optional-attributes"></a>İsteğe bağlı öznitelikleri

Aşağıdaki öznitelikler, yalnızca ASP.NET uygulamaları için geçerlidir. Yapılandırma sistemi diğer uygulama türleri için bu öznitelikler yoksayar.

|                     | Açıklama |
| ------------------- | ----------- |
| **allowDefinition** | Bölüm kullanılabilir hangi yapılandırma dosyasını belirtir. Aşağıdaki değerlerden birini kullanın:<br><br>**Her yerde**<br>Her yapılandırma dosyasında kullanılacak bölümü sağlar. Bu varsayılandır.<br>**MachineOnly**<br>Yalnızca makine yapılandırma dosyasında kullanılacak bölümü sağlar (*Machine.config*).<br>**MachineToApplication**<br>Makine yapılandırma dosyası veya uygulama yapılandırma dosyasında kullanılacak bölümü sağlar. |
| **allowLocation**   | Bölüm içinde kullanılıp kullanılamayacağını belirler  **\<konumu >** öğesi. Aşağıdaki değerlerden birini kullanın:<br><br>**true**<br>İçinde kullanılacak bölümü sağlar  **\<konumu >** öğesi. Bu varsayılandır.<br>**false**<br>İçinde kullanılacak bölümüne izin vermiyor  **\<konumu >** öğesi. |

## <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| [**\<configSections >** öğesi](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimlerini içerir. |
| [**\<sectionGroup >** öğesi](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Yapılandırma bölümleri için bir ad alanını tanımlar. |

> [!NOTE]
> A  **\<bölüm >** öğesi bir alt öğedir ya da  **\<configSections >** veya  **\<sectionGroup >** değil her ikisi de.

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

Yapılandırma bölümü temelde bildirme yapılandırma dosyası için yeni bir öğesi tanımlar. Yeni öğe bir yapılandırma işleyici bölüm ayarları içerir (diğer bir deyişle, uygulayan bir sınıf <xref:System.Configuration.IConfigurationSectionHandler> arabirimi) okur. Öznitelikler ve alt öğeler tanımladığınız bir bölümün ayarlarınızı okumak için kullandığınız bölüm işleyicisi bağlıdır.

Yapılandırma bölümü işleyici bildirme *Machine.config* dosyası sağlar, bu bilgisayarda, tüm uygulama yapılandırma dosyasındaki yapılandırma bölümü kullanmanızı, sürece **allowDefinition**özniteliği belirtir. Aksi takdirde.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma bölümü ve o bölümün ayarlarının tanımlamaya gösterilmektedir:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" 
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
