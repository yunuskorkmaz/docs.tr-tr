---
title: "Uygulama Ayarları Şeması"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 028fdbeb90a1499459803f24f3aa62923452edba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="app-settings-schema"></a>Uygulama Ayarları Şeması

Dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgilerini bir uygulama gibi özel uygulama ayarlarını içerir.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<ekleme >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Clear >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)

| Öğe | Açıklama |
| ------- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | İçeren  **\<Ekle >**,  **\<temizleyin >**, ve  **\<kaldırmak >** etiketler denetim uygulama ayarları. İsteğe bağlı bir sahip **dosya** özniteliği. |
| [**\<ekleme >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Bir ayar tanımlar. Alt  **\<appSettings >**. Gerektirir **anahtar** ve **değeri** öznitelikleri. |
| [**\<Clear >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Tüm ayarları siler. Alt  **\<appSettings >**. Öznitelikleri yok. |
| [**\<kaldırma >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Bir ayar kaldırır. Alt  **\<appSettings >**. Gerektiren bir **anahtar** özniteliği. |

## <a name="appsettings-element"></a>\<appSettings > öğesi

Bu öğeyi içeren  **\<Ekle >**,  **\<temizleyin >**, ve  **\<Kaldır >** etiketler denetim uygulama ayarları. İçin isteğe bağlı bir öznitelik tanımlar **dosya**.

## <a name="add-element"></a>\<Ekle > öğesi

Özel uygulama ayarı ad/değer çifti olarak uygulama ayarları koleksiyonuna ekler. Özniteliklerini tanımlayan **anahtar** ve **değeri**.

## <a name="clear-element"></a>\<Clear > öğesi

Devralınan özel uygulama ayarlarına yapılan tüm başvuruları kaldırır ve tarafından eklenen başvurulara izin verir  **\<Ekle >** aşağıdaki öğeleri  **\<temizleyin >** öğesi. Öznitelikleri tanımlar.

## <a name="remove-element"></a>\<kaldırma > öğesi

Devralınan özel uygulama ayarı için bir başvuru uygulama ayarları koleksiyonundan kaldırır. İçin bir öznitelik tanımlar **anahtar**.

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

## <a name="see-also"></a>Ayrıca bkz.

[Uygulama ayarlarına genel bakış](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[Uygulama Ayarları Mimarisi](~/docs/framework/winforms/advanced/application-settings-architecture.md)
