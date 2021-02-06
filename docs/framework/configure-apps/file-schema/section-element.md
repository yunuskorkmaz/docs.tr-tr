---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: <section> öğesi'
title: <section> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 7756f7ee3be2391a0d068708f3719083640b5595
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639945"
---
# <a name="section-element"></a>\<section> öğesi

Bir yapılandırma bölümü bildirimi içerir.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a>Syntax

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Gerekli öznitelikler

|           | Description |
| --------- | ----------- |
| **ada**  | Yapılandırma bölümünün adını belirtir. |
| **türüyle**  | Yapılandırma dosyasından bölümü okuyan yapılandırma bölümü işleyici sınıfının adını belirtir. Tür değeri "tam nitelikli-bölüm-işleyici-sınıf-adı, basit-derleme-adı" sözdizimine sahiptir. Basit derleme adı, *. dll* dosya uzantısı olmayan kök dosya adıdır. |

## <a name="optional-attributes"></a>İsteğe bağlı öznitelikler

Aşağıdaki öznitelikler yalnızca ASP.NET uygulamaları için geçerlidir. Yapılandırma sistemi, diğer uygulama türleri için bu öznitelikleri yoksayar.

|                     | Description |
| ------------------- | ----------- |
| **allowDefinition** | Bölümün hangi yapılandırma dosyasına kullanılabileceğini belirtir. Aşağıdaki değerlerden birini kullanın:<br><br>**Yer**<br>Bölümün herhangi bir yapılandırma dosyasında kullanılmasına izin verir. Bu varsayılan seçenektir.<br>**MachineOnly**<br>Bölümün yalnızca makine yapılandırma dosyasında (*Machine.config*) kullanılmasına izin verir.<br>**MachineToApplication**<br>Bölümün makine yapılandırma dosyasında veya uygulama yapılandırma dosyasında kullanılmasına izin verir. |
| **allowLocation**   | Bölümün öğe içinde kullanılıp kullanılamayacağını belirler **\<location>** . Aşağıdaki değerlerden birini kullanın:<br><br>**değeri**<br>Bölümünün öğesi içinde kullanılmasına izin verir **\<location>** . Bu varsayılan seçenektir.<br>**yanlýþ**<br>, Bölümün öğesi içinde kullanılmasına izin vermez **\<location>** . |

## <a name="parent-elements"></a>Üst öğeler

|     | Description |
| --- | ----------- |
| [**\<configSections>** Dosyalarında](configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimleri içerir. |
| [**\<sectionGroup>** Dosyalarında](sectiongroup-element-for-configsections.md) | Yapılandırma bölümleri için bir ad alanı tanımlar. |

> [!NOTE]
> **\<section>** Öğesi, veya öğelerinin alt öğesidir **\<configSections>** **\<sectionGroup>** .

## <a name="child-elements"></a>Alt öğeleri

Yok

## <a name="remarks"></a>Açıklamalar

Bir yapılandırma bölümünün bildirilmesi, temel olarak yapılandırma dosyası için yeni bir öğe tanımlar. Yeni öğe, bir yapılandırma bölümü işleyicisinin (yani, arabirimini uygulayan bir sınıf <xref:System.Configuration.IConfigurationSectionHandler> ) okuduğu ayarları içerir. Tanımladığınız bir bölümün öznitelikleri ve alt öğeleri, ayarlarınızı okumak için kullandığınız bölüm işleyicisine bağlıdır.

*Machine.config* dosyasında bir yapılandırma bölümü işleyicisi bildirmek, **allowDefinition** özniteliği aksini belirtmedikçe, bu bilgisayardaki herhangi bir uygulama yapılandırma dosyasında yapılandırma bölümünü kullanmanıza olanak sağlar.

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

Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine.config*) ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarda kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
