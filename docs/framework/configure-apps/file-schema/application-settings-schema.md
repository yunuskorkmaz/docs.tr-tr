---
title: Uygulama Ayarları Şeması
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7a4f60571fb4d30793f64c57317bf0b372ae4812
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701917"
---
# <a name="application-settings-schema"></a>Uygulama Ayarları Şeması

Uygulama ayarlarını depolamak ve uygulama kapsamlı ve kullanıcı kapsamlı ayarları almak bir Windows Forms veya ASP.NET uygulaması sağlar. Bu bağlamda bir *ayarı* herhangi belirli uygulamaya veya geçerli kullanıcının belirli bir bilgi parçasıdır — bir veritabanı bağlantı dizesi kullanıcıya kadar her şeyi varsayılan pencere boyutu tercih edilen.

Varsayılan olarak, bir Windows Forms uygulamasında uygulama ayarlarını kullanan <xref:System.Configuration.LocalFileSettingsProvider> sınıfını, ki bu ayarları bir XML yapılandırma dosyasında saklamak için .NET yapılandırma sistemini kullanır. Uygulama ayarları tarafından kullanılan dosyalar hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](~/docs/framework/winforms/advanced/application-settings-architecture.md).

Uygulama ayarları, kullandığı yapılandırma dosyalarını bir parçası olarak aşağıdaki öğeleri tanımlar.

| Öğe                    | Açıklama                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | Tüm içeren  **\<ayarı >** etiketler uygulamaya özgü.                         |
| **\<kullanıcı ayarlarını >**        | Tüm içeren  **\<ayarı >** geçerli kullanıcıya özel etiketler.                        |
| **\<ayarı >**             | Bir ayarı tanımlar. Ya da alt  **\<applicationSettings >** veya  **\<ayarlarını >**. |
| **\<Değer >**               | Bir ayarın değerini tanımlar. Alt  **\<ayarı >**.                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > öğesi

Bu öğe tüm içeren  **\<ayarı >** istemci bilgisayarda uygulamanın bir örneği için özel etiketler. Bu öznitelikleri tanımlar.

## <a name="usersettings-element"></a>\<kullanıcı ayarlarını > öğesi

Bu öğe tüm içeren  **\<ayarı >** uygulama kullanmakta olduğu kullanıcıya özel etiketler. Bu öznitelikleri tanımlar.

## <a name="setting-element"></a>\<ayarı > öğesi

Bu öğe bir ayarı tanımlar. Bunu, aşağıdaki özniteliklere sahiptir.

| Öznitelik        | Açıklama |
| ---------------- | ----------- |
| **Adı**         | Gerekli. Ayar benzersiz kimliği. Visual Studio aracılığıyla oluşturulan ayarları adı ile kaydedilmiş `ProjectName.Properties.Settings`. |
| **serializedAs** | Gerekli. Metin değeri serileştirmek için kullanılacak biçimi. Geçerli değerler şunlardır:<br><br>- `string`. Değer bir dize kullanarak olarak serileştirilmiş bir <xref:System.ComponentModel.TypeConverter>.<br>- `xml`. Değer, XML serileştirme kullanarak seri hale getirilir.<br>- `binary`. Değer, ikili serileştirme kullanarak metin ile kodlanmış ikili olarak seri hale getirilir.<br />- `custom`. Ayar sağlayıcısı bu ayar devralmaz sahiptir ve serileştirir ve bunu serileştirir. |

## <a name="value-element"></a>\<Değer > öğesi

Bu öğe bir ayarın değerini içerir.

## <a name="example"></a>Örnek

Aşağıdaki örnek iki uygulama kapsamlı ayarlar ve iki kullanıcı kapsamlı ayarları tanımlayan uygulama ayarları dosyası gösterilmektedir:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama Ayarlarına Genel Bakış](~/docs/framework/winforms/advanced/application-settings-overview.md)
- [Uygulama Ayarları Mimarisi](~/docs/framework/winforms/advanced/application-settings-architecture.md)
