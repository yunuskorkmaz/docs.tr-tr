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
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153742"
---
# <a name="section-element"></a>\<bölüm> öğesi

Yapılandırma bölümü bildirimi içerir.

[**\<yapılandırma>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configBölüm>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bölüm>**

[**\<yapılandırma>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configBölüm>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bölümGrup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bölüm>**

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
| **Türü**  | Yapılandırma dosyasından bölümü okuyan yapılandırma bölümü işleyicisınıfının adını belirtir. Tür değeri sözdizimi vardır "tam nitelikli-bölüm işleyicisi-sınıf adı, basit-derleme-adı". Basit derleme adı *.dll* dosya uzantısı olmayan kök dosya adıdır. |

## <a name="optional-attributes"></a>İsteğe bağlı öznitelikler

Aşağıdaki öznitelikler yalnızca ASP.NET uygulamalar için geçerlidir. Yapılandırma sistemi, diğer uygulama türleri için bu öznitelikleri yoksayar.

|                     | Açıklama |
| ------------------- | ----------- |
| **Allowdefinition** | Bölümün hangi yapılandırma dosyasında kullanılabileceğini belirtir. Aşağıdaki değerlerden birini kullanın:<br><br>**Heryer -de**<br>Bölümün herhangi bir yapılandırma dosyasında kullanılmasını sağlar. Bu varsayılandır.<br>**MakineSadece**<br>Bölümün yalnızca makine yapılandırma dosyasında *(Machine.config)* kullanılmasını sağlar.<br>**MachinetoApplication**<br>Bölümün makine yapılandırma dosyasında veya uygulama yapılandırma dosyasında kullanılmasını sağlar. |
| **Allowlocation**   | Bölümün ** \<konum>** öğesi içinde kullanılıp kullanılamayacağı belirlenir. Aşağıdaki değerlerden birini kullanın:<br><br>**true**<br>Bölümün ** \<konum>** öğesi içinde kullanılmasını sağlar. Bu varsayılandır.<br>**yanlış**<br>Bölümün ** \<konum>** öğesi içinde kullanılmasına izin vermez. |

## <a name="parent-elements"></a>Üst öğeler

|     | Açıklama |
| --- | ----------- |
| [** \<configSections>** Öğe](configsections-element-for-configuration.md) | Yapılandırma bölümü ve ad alanı bildirimleri içerir. |
| [** \<bölümGrup>** Öğe](sectiongroup-element-for-configsections.md) | Yapılandırma bölümleri için bir ad alanı tanımlar. |

> [!NOTE]
> ** \<Bir bölüm>** öğesi ** \<configSections>** veya ** \<sectionGroup>** bir alt öğesidir, ancak her ikisi de değil.

## <a name="child-elements"></a>Alt öğeleri

None

## <a name="remarks"></a>Açıklamalar

Yapılandırma bölümü bildirmek, yapılandırma dosyası için temelde yeni bir öğe tanımlar. Yeni öğe, yapılandırma bölümü işleyicisinin (diğer bir şekilde <xref:System.Configuration.IConfigurationSectionHandler> arabirimi uygulayan bir sınıfın) okuduğu ayarları içerir. Tanımladığınız bir bölümün öznitelikleri ve alt öğeleri, ayarlarınızı okumak için kullandığınız bölüm işleyicisine bağlıdır.

*Machine.config* dosyasında bir yapılandırma bölümü işleyicisi bildirmek, **allowDefinition** özniteliği aksini belirtmediği sürece, o bilgisayardaki herhangi bir uygulama yapılandırma dosyasında yapılandırma bölümünü kullanmanıza olanak tanır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, yapılandırma bölümünün nasıl tanımlanılıgı ve bu bölümün ayarlarını nasıl tanımlanabilirsiniz:

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

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
