---
title: <section> öğesi
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
ms.openlocfilehash: 58f823ce0c128f30e361b4a631d41286533b5f0f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259221"
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

## <a name="required-attributes"></a>Gerekli öznitelikleri

|           | Açıklama |
| --------- | ----------- |
| **Adı**  | Yapılandırma bölümünün adını belirtir. |
| **type**  | Bölüm yapılandırma dosyasından okur yapılandırma bölümü işleyici sınıf adını belirtir. Türü değeri "fully-qualified-section-handler-class-name, basit bütünleştirilmiş kod adı" sözdizimi vardır. Kök dosya adı olmadan basit derleme adı: *.dll* dosya uzantısı. |

## <a name="optional-attributes"></a>İsteğe bağlı öznitelikleri

Aşağıdaki öznitelikleri, yalnızca ASP.NET uygulamaları için geçerlidir. Yapılandırma sistemi, diğer uygulama türleri için bu öznitelikler yok sayar.

|                     | Açıklama |
| ------------------- | ----------- |
| **allowDefinition** | Bölüm kullanılabilir hangi yapılandırma dosyasını belirtir. Aşağıdaki değerlerden birini kullanın:<br><br>**Her yerde**<br>Herhangi bir yapılandırma dosyasında kullanılacak bölüm sağlar. Bu varsayılandır.<br>**MachineOnly**<br>Yalnızca makine yapılandırma dosyasında kullanılacak bölüm sağlar (*Machine.config*).<br>**MachineToApplication**<br>Makine yapılandırma dosyası veya uygulama yapılandırma dosyasında kullanılacak bölüm sağlar. |
| **allowLocation**   | Bölüm içinde kullanılmasına izin verilip verilmeyeceğini belirler  **\<konum >** öğesi. Aşağıdaki değerlerden birini kullanın:<br><br>**true**<br>İçinde kullanılacak bölüm tanır  **\<konum >** öğesi. Bu varsayılandır.<br>**false**<br>İçinde kullanılacak bölümüne izin vermiyor  **\<konum >** öğesi. |

## <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| [**\<configSections >** öğesi](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimi içerir. |
| [**\<sectionGroup >** öğesi](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Yapılandırma bölümleri için bir ad alanı tanımlar. |

> [!NOTE]
> A  **\<bölüm >** öğedir ya da alt öğesi  **\<configSections >** veya  **\<sectionGroup >** değil her ikisi de.

## <a name="child-elements"></a>Alt öğeleri

Hiçbiri

## <a name="remarks"></a>Açıklamalar

Bir yapılandırma bölümünü temelde bildirme yapılandırma dosyası için yeni bir öğe tanımlar. Yeni bir öğe bir yapılandırma işleyici bölüm ayarları içerir (diğer bir deyişle, uygulayan bir sınıf <xref:System.Configuration.IConfigurationSectionHandler> arabirimi) okur. Öznitelikler ve alt öğeleri tanımladığınız bir bölümün ayarlarınızı okumak için kullandığınız bölümü işleyicisinde bağlıdır.

Bir yapılandırma bölümü işleyicisinde bildirme *Machine.config* dosya yapılandırma bölümü bu bilgisayarda, bir uygulama yapılandırma dosyasında kullanmanıza olanak sağlar sürece **allowDefinition**özniteliği, aksi takdirde belirtir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma bölümü tanımlayın ve bu bölümün ayarlarını tanımlamak gösterilmektedir:

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

Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
