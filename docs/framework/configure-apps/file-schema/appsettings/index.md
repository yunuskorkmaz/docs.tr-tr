---
title: Uygulama Ayarları Şeması
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9bf2568c8c18f8f6d18c445e802cc72df18fb8c4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50191154"
---
# <a name="app-settings-schema"></a>Uygulama Ayarları Şeması

Dosya yolları, XML Web hizmeti URL'leri ya da bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama ayarları içerir.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Ekle >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Temizleme >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)

| Öğe | Açıklama |
| ------- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | İçeren  **\<Ekle >**,  **\<Temizle >**, ve  **\<kaldırma >** denetimi uygulama ayarlarına etiketler. İsteğe bağlı olan **dosya** özniteliği. |
| [**\<Ekle >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Bir ayarı tanımlar. Alt  **\<appSettings >**. Gerektirir **anahtarı** ve **değer** öznitelikleri. |
| [**\<Temizleme >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Tüm ayarları siler. Alt  **\<appSettings >**. öznitelikleri yok. |
| [**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Bir ayar kaldırır. Alt  **\<appSettings >**. Gerektiren bir **anahtar** özniteliği. |

## <a name="appsettings-element"></a>\<appSettings > öğesi

Bu öğeyi içeren  **\<Ekle >**,  **\<Temizle >**, ve  **\<kaldırma >** denetimi uygulama ayarlarına etiketler. İçin isteğe bağlı bir öznitelik tanımlar **dosya**.

## <a name="add-element"></a>\<Ekle > öğesi

Özel uygulama ayarı adı/değer çifti olarak uygulama ayarlarını koleksiyona ekler. İçin öznitelikleri tanımlar **anahtarı** ve **değer**.

## <a name="clear-element"></a>\<Temizle > öğesi

Devralınan özel uygulama ayarlarına yapılan tüm başvuruları kaldırır ve tarafından eklenen başvuruları sağlayan  **\<Ekle >** aşağıdaki öğeleri  **\<Temizle >** öğe. Bu öznitelikleri tanımlar.

## <a name="remove-element"></a>\<kaldırma > öğesi

Devralınan özel uygulama ayarı için bir başvuru uygulaması ayarları koleksiyondan kaldırır. İçin bir öznitelik tanımlar **anahtar**.

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

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarlarına Genel Bakış](~/docs/framework/winforms/advanced/application-settings-overview.md)   
- [Uygulama Ayarları Mimarisi](~/docs/framework/winforms/advanced/application-settings-architecture.md)
