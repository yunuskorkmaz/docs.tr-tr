---
title: <configuration> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dcdf8d0f11ae65353da08bba1f8d2fe5ab415c6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705564"
---
# <a name="appsettings-element-for-configuration"></a>\<appSettings > öğesi için \<yapılandırma >

Özel uygulama ayarları içerir. .NET Framework tarafından sağlanan önceden tanımlanmış yapılandırma bölümü budur.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<appSettings>**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **Dosya**  | İsteğe bağlı öznitelik.<br><br>Özel uygulama yapılandırma ayarlarını içeren bir dış dosya için göreli bir yol belirtir. Belirtilen dosya aynı tür içinde belirtilen ayarları içeren  **\<Ekle >**,  **\<kaldırma >**, ve  **\<Temizle >** öğeleri ve kullanıyor aynı anahtar/değer çifti bu öğeler biçimlendirin.<br><br>Belirtilen yol göreli ana yapılandırma dosyasıdır. Bir Windows Forms uygulaması için bu ikili klasördür (örneğin */bin/debug*), uygulama yapılandırma dosyası konumu değil. Web Forms uygulamaları için uygulama köküne göreli yoludur burada *web.config* dosyasının bulunduğu.<br><br>Belirtilen dosya bulunamadı, çalışma zamanı öznitelik yoksaydığını unutmayın. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<Yapılandırma >** öğesi](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<Ekle >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Özel uygulama ayarı ekler. |
| [**\<Temizleme >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Tüm önceden tanımlanmış uygulama ayarlarını temizler. |
| [**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Önceden tanımlanmış uygulama ayarı kaldırır. |

## <a name="remarks"></a>Açıklamalar

**\<AppSettings >** öğesi veritabanı bağlantı dizeleri, dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgileri için gibi özel bir uygulama yapılandırma bilgilerini depolayan bir uygulama. Belirtilen anahtar/değer çiftleri  **\<appSettings >** öğesi kullanılarak koddan erişilebilir <xref:System.Configuration.ConfigurationSettings> sınıfı.

Kullanabileceğiniz **dosya** özniteliğini  **\<appSettings >** öğesinin *Web.config* ve uygulama yapılandırma dosyaları. Bu öznitelik belirtilen ayarları geçersiz kılar veya ek ayarlar sağlayan bir yapılandırma dosyası belirtir  **\<appSettings >** öğesi. **Dosya** özniteliği, ne zaman bir uygulama yapılandırma dosyasında belirtilen proje ayarlarını geçersiz kılmak bir kullanıcının istediği gibi kaynak denetimi takım geliştirme senaryolarda kullanılabilir.

Yapılandırma dosyaları tarafından belirtilen **dosya** öznitelik, bir kök düğümü olmalıdır **\<appSettings >** yerine **\<yapılandırma >**.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir dış uygulama ayarları dosyasından gösterir (*custom.config*), özel uygulama ayarını tanımlar:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Aşağıdaki örnek, dış ayarları dosyası ayarı kullanır ve bir uygulama ayarı kendi ayarlar uygulama yapılandırma dosyasını gösterir:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe, uygulama yapılandırma dosyasında, makine yapılandırma dosyası kullanılabilir (*Machine.config*), ve *Web.config* uygulama dizin düzeyinde olmayan dosyalar.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
