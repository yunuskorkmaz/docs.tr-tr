---
title: Uygulama ayarları şeması
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 609ddba9cd4d58f9c388cf669039ee128e87efd0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088074"
---
# <a name="app-settings-schema"></a>Uygulama ayarları şeması

Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<add >** ](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clear >** ](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Kaldır >** ](remove-element-for-appsettings.md)

| Öğe | Açıklama |
| ------- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Uygulama ayarlarını denetlemek için **> ekle\<** , **\<Temizle >** ve\<etiketlerini **Kaldır** . , İsteğe bağlı bir **Dosya** özniteliğine sahiptir. |
| [ **\<> Ekle**](add-element-for-appsettings.md) | Bir ayarı tanımlar. **\<appSettings >** alt öğesi. **Anahtar** ve **değer** öznitelikleri gerektirir. |
| [ **\<Temizle >** ](clear-element-for-appsettings.md) | Tüm ayarları temizler. **\<appSettings >** alt öğesi. Hiç özniteliği yok. |
| [ **\<> Kaldır**](remove-element-for-appsettings.md) | Bir ayarı kaldırır. **\<appSettings >** alt öğesi. **Anahtar** özniteliği gerektirir. |

## <a name="appsettings-element"></a>\<appSettings > öğesi

Bu öğe, uygulama ayarlarını denetlemek için **> ekle\<** , **\<Temizle >** ve\<etiketlerini **Kaldır** ' ı içerir. **Dosya**için isteğe bağlı bir öznitelik tanımlar.

## <a name="add-element"></a>\<> öğesi Ekle

Uygulama ayarları koleksiyonuna bir ad/değer çifti olarak özel bir uygulama ayarı ekler. **Anahtar** ve **değer**için öznitelikleri tanımlar.

## <a name="clear-element"></a>\<Clear > öğesi

Devralınan özel uygulama ayarlarına yapılan tüm başvuruları kaldırır ve yalnızca **\<clear >** öğesinden sonra > öğeleri **eklemek\<** tarafından eklenen başvuruların kullanılmasına izin verir. Hiçbir öznitelik tanımlamıyor.

## <a name="remove-element"></a>\<> öğesi kaldır

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
