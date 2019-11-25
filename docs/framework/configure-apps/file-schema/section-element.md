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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c1675540df6844f98572c11cfb140bff23b31a8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089028"
---
# <a name="section-element"></a>\<Bölüm > öğesi

Bir yapılandırma bölümü bildirimi içerir.

[ **\<configuration >** ](configuration-element.md) \
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<bölüm >**

[ **\<configuration >** ](configuration-element.md) \
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sectionGroup >** ](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bölümü >**

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
| **ada**  | Yapılandırma bölümünün adını belirtir. |
| **türüyle**  | Yapılandırma dosyasından bölümü okuyan yapılandırma bölümü işleyici sınıfının adını belirtir. Tür değeri "tam nitelikli-bölüm-işleyici-sınıf-adı, basit-derleme-adı" sözdizimine sahiptir. Basit derleme adı, *. dll* dosya uzantısı olmayan kök dosya adıdır. |

## <a name="optional-attributes"></a>İsteğe bağlı öznitelikler

Aşağıdaki öznitelikler yalnızca ASP.NET uygulamaları için geçerlidir. Yapılandırma sistemi, diğer uygulama türleri için bu öznitelikleri yoksayar.

|                     | Açıklama |
| ------------------- | ----------- |
| **allowDefinition** | Bölümün hangi yapılandırma dosyasına kullanılabileceğini belirtir. Aşağıdaki değerlerden birini kullanın:<br><br>**Yer**<br>Bölümün herhangi bir yapılandırma dosyasında kullanılmasına izin verir. Bu varsayılandır.<br>**MachineOnly**<br>Bölümün yalnızca makine yapılandırma dosyasında (*Machine. config*) kullanılmasına izin verir.<br>**MachineToApplication**<br>Bölümün makine yapılandırma dosyasında veya uygulama yapılandırma dosyasında kullanılmasına izin verir. |
| **allowLocation**   | Bölümün **\<location >** öğesi içinde kullanılıp kullanılamayacağını belirler. Aşağıdaki değerlerden birini kullanın:<br><br>**true**<br>Bölümün **\<location >** öğesi içinde kullanılmasına izin verir. Bu varsayılandır.<br>**false**<br>Bölümün **\<location >** öğesi içinde kullanılmasına izin vermez. |

## <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| [ **\<configSections >** Dosyalarında](configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimleri içerir. |
| [ **\<sectionGroup >** Dosyalarında](sectiongroup-element-for-configsections.md) | Yapılandırma bölümleri için bir ad alanı tanımlar. |

> [!NOTE]
> **\<bölüm >** öğesi, **\<configSections >** veya **\<sectionGroup >** alt öğesidir, ancak her ikisine birden değil.

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

Bir yapılandırma bölümünün bildirilmesi, temel olarak yapılandırma dosyası için yeni bir öğe tanımlar. Yeni öğe, bir yapılandırma bölümü işleyicisinin (yani, <xref:System.Configuration.IConfigurationSectionHandler> arabirimini uygulayan bir sınıf) okuduğu ayarları içerir. Tanımladığınız bir bölümün öznitelikleri ve alt öğeleri, ayarlarınızı okumak için kullandığınız bölüm işleyicisine bağlıdır.

*Machine. config* dosyasında bir yapılandırma bölümü işleyicisi bildirmek, **allowDefinition** özniteliği aksini belirtmedikçe, bu bilgisayardaki herhangi bir uygulama yapılandırma dosyasında yapılandırma bölümünü kullanmanıza olanak sağlar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir yapılandırma bölümünün nasıl tanımlanacağını ve bu bölüm için ayarların nasıl tanımlanacağını göstermektedir:

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

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
