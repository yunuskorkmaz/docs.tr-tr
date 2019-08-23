---
title: Uygulama ayarları şeması
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d02f9f952c0ca7651d27571111a2d29f3d1130fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921295"
---
# <a name="app-settings-schema"></a>Uygulama ayarları şeması

Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir.

[ **\<Yapılandırma >** ](../configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Ekle**](add-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Temizle**](clear-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> Kaldır**](remove-element-for-appsettings.md)

| Öğe | Açıklama |
| ------- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Uygulama ayarlarını denetlemek için  **\<> Ekle**,  **\<> Temizle**ve  **\<> etiketlerini kaldır** ' ı içerir. , İsteğe bağlı bir **Dosya** özniteliğine sahiptir. |
| [ **\<> Ekle**](add-element-for-appsettings.md) | Bir ayarı tanımlar. AppSettings > alt öğesi.  **\<** **Anahtar** ve **değer** öznitelikleri gerektirir. |
| [ **\<> Temizle**](clear-element-for-appsettings.md) | Tüm ayarları temizler. AppSettings > alt öğesi.  **\<** Hiç özniteliği yok. |
| [ **\<> Kaldır**](remove-element-for-appsettings.md) | Bir ayarı kaldırır. AppSettings > alt öğesi.  **\<** **Anahtar** özniteliği gerektirir. |

## <a name="appsettings-element"></a>\<appSettings > öğesi

Bu öğe, uygulama ayarlarını denetlemek için  **\<> Ekle**,  **\<> Temizle**ve  **\<> etiketlerini kaldır** ' ı içerir. **Dosya**için isteğe bağlı bir öznitelik tanımlar.

## <a name="add-element"></a>\<> öğesi Ekle

Uygulama ayarları koleksiyonuna bir ad/değer çifti olarak özel bir uygulama ayarı ekler. **Anahtar** ve **değer**için öznitelikleri tanımlar.

## <a name="clear-element"></a>\<> öğeyi temizle

Devralınan özel uygulama ayarlarına yapılan tüm başvuruları kaldırır ve yalnızca  **\<Clear >** öğesini takip eden  **\<>** öğeleri ekleyerek eklenen başvuruların kullanılmasına izin verir. Hiçbir öznitelik tanımlamıyor.

## <a name="remove-element"></a>\<> öğeyi kaldır

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
