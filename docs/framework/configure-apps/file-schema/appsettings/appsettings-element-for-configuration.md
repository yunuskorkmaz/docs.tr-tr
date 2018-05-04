---
title: '&lt;appSettings&gt; öğesi için &lt;yapılandırma&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: d17400536b911ce0be4d2bf105b0b4d99d0916df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > öğesi için \<yapılandırma >

Özel uygulama ayarlarını içerir. .NET Framework tarafından sağlanan önceden tanımlanmış yapılandırma bölümüdür.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<appSettings >**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **Dosya**  | İsteğe bağlı öznitelik.<br><br>Özel uygulama yapılandırma ayarlarını içeren bir dış dosya için göreli bir yol belirtir. Belirtilen dosya aynı tür belirtilen ayarları içerir  **\<Ekle >**,  **\<kaldırma >**, ve  **\<temizleyin >** öğeleri ve aynı anahtar/değer çifti biçimini bu öğeler olarak kullanır.<br><br>Belirtilen yolu göreli ana yapılandırma dosyası değil. Bir Windows Forms uygulaması için bu ikili klasördür (örneğin */bin/debug*), uygulama yapılandırma dosyası konumu değil. Web Forms uygulamaları için uygulama kökü göreli yoludur nerede *web.config* dosyasının bulunduğu.<br><br>Belirtilen dosya bulunamadı, çalışma zamanı özniteliği yok sayar unutmayın. |

## <a name="parent-element"></a>Üst öğesi

|     | Açıklama |
| --- | ----------- |
| [**\<Yapılandırma >** öğesi](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<ekleme >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Özel uygulama ayarı ekler. |
| [**\<Clear >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Tüm önceden tanımlanmış uygulama ayarlarını temizler. |
| [**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Önceden tanımlanmış uygulama ayarı kaldırır. |

## <a name="remarks"></a>Açıklamalar

**\<AppSettings >** öğesi veritabanı bağlantı dizeleri, dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgileri için gibi özel uygulama yapılandırma bilgilerini depolayan bir uygulama. Belirtilen anahtar/değer çiftlerinin  **\<appSettings >** öğesi kullanılarak kod erişilir <xref:System.Configuration.ConfigurationSettings> sınıfı.

Kullanabileceğiniz **dosya** özniteliğini  **\<appSettings >** öğesinin *Web.config* ve uygulama yapılandırma dosyaları. Bu öznitelik ek ayarlar sağlayan veya belirtilen ayarları geçersiz kılan bir yapılandırma dosyası belirtir  **\<appSettings >** öğesi. **Dosya** özniteliği, ne zaman bir uygulama yapılandırma dosyasında belirtilen proje ayarlarını geçersiz kılmak üzere bir kullanıcının istediği gibi kaynak denetim takım geliştirme senaryolarda kullanılabilir.

Yapılandırma dosyaları tarafından belirtilen **dosya** öznitelik, bir kök düğümü olmalıdır  **\<appSettings >** yerine  **\<configuration >**.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir dış uygulama ayarları dosyası gösterir (*custom.config*), özel uygulama ayarını tanımlar:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Aşağıdaki örnek, dış ayarları dosyasında ayarı kullanır ve bir uygulama ayarı kendi ayarlar uygulama yapılandırma dosyası gösterir:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
