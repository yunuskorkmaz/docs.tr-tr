---
title: Uygulama ayarları şeması
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215423"
---
# <a name="app-settings-schema"></a>Uygulama ayarları şeması

Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](remove-element-for-appsettings.md)

| Öğe | Açıklama |
| ------- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | **\<add>** **\<clear>** **\<remove>** Uygulama ayarlarını denetlemek için, ve etiketlerini içerir. , İsteğe bağlı bir **Dosya** özniteliğine sahiptir. |
| [**\<add>**](add-element-for-appsettings.md) | Bir ayarı tanımlar. Alt öğesi **\<appSettings>** . **Anahtar** ve **değer** öznitelikleri gerektirir. |
| [**\<clear>**](clear-element-for-appsettings.md) | Tüm ayarları temizler. Alt öğesi **\<appSettings>** . Hiç özniteliği yok. |
| [**\<remove>**](remove-element-for-appsettings.md) | Bir ayarı kaldırır. Alt öğesi **\<appSettings>** . **Anahtar** özniteliği gerektirir. |

## <a name="appsettings-element"></a>\<appSettings> öğesi

Bu öğe, **\<add>** **\<clear>** **\<remove>** uygulama ayarlarını denetlemek için, ve etiketlerini içerir. **Dosya**için isteğe bağlı bir öznitelik tanımlar.

## <a name="add-element"></a>\<add> öğesi

Uygulama ayarları koleksiyonuna bir ad/değer çifti olarak özel bir uygulama ayarı ekler. **Anahtar** ve **değer**için öznitelikleri tanımlar.

## <a name="clear-element"></a>\<clear> öğesi

Devralınan özel uygulama ayarlarına yapılan tüm başvuruları kaldırır ve yalnızca öğesini izleyen öğeler tarafından eklenen başvurulara izin verir **\<add>** **\<clear>** . Hiçbir öznitelik tanımlamıyor.

## <a name="remove-element"></a>\<remove> öğesi

Devralınan özel uygulama ayarının başvurusunu uygulama ayarları koleksiyonundan kaldırır. **Anahtar**için bir özniteliği tanımlar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir özel uygulama ayarı tanımlayan bir dış uygulama ayarları dosyasını (*Custom. config*) gösterir:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Aşağıdaki örnek, dış ayarlar dosyasında ayarı tüketen ve kendi uygulama ayarını ayarlayan bir uygulama yapılandırma dosyasını gösterir:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarlarına Genel Bakış](../../../winforms/advanced/application-settings-overview.md)
- [Uygulama Ayarları Mimarisi](../../../winforms/advanced/application-settings-architecture.md)
