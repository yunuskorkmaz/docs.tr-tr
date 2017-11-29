---
title: "Uygulama Ayarları Şeması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
caps.latest.revision: "3"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d93a18b17e0d6b8e413903fb84dc6b427d94f6af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="application-settings-schema"></a>Uygulama Ayarları Şeması

Uygulama ayarlarını depolamak ve uygulama kapsamlı ve kullanıcı kapsamlı ayarlarını almak bir Windows Forms ya da ASP.NET uygulamasının izin verin. Bu bağlamda bir *ayarı* herhangi belirli uygulama veya belirli kullanıcı için geçerli olabilecek bilgidir — herhangi bir şeyin bir veritabanı bağlantı dizesi kullanıcıya varsayılan pencere boyutu tercih edilen.

Varsayılan olarak, bir Windows Forms uygulamasında uygulama ayarları kullanan <xref:System.Configuration.LocalFileSettingsProvider> .NET yapılandırma sistemini ayarları bir XML yapılandırma dosyasında depolamak için kullandığı sınıf. Uygulama ayarları tarafından kullanılan dosyaları hakkında daha fazla bilgi için bkz: [uygulama ayarları mimarisi](~/docs/framework/winforms/advanced/application-settings-architecture.md).

Uygulama ayarları aşağıdaki öğeleri kullanır yapılandırma dosyalarını bir parçası olarak tanımlar.

| Öğe                    | Açıklama                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | Tüm içeren  **\<ayarı >** etiketler uygulamaya özgü.                         |
| **\<kullanıcı ayarlarını >**        | Tüm içeren  **\<ayarı >** geçerli kullanıcıya özel etiketler.                        |
| **\<Ayar >**             | Bir ayar tanımlar. Ya da alt  **\<applicationSettings >** veya  **\<ayarlarını >**. |
| **\<Değer >**               | Bir ayarın değerini tanımlar. Alt  **\<ayarı >**.                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > öğesi

Bu öğe tüm içeren  **\<ayarı >** bir istemci bilgisayarda uygulama örneği için özel etiketler. Öznitelikleri tanımlar.

## <a name="usersettings-element"></a>\<kullanıcı ayarlarını > öğesi

Bu öğe tüm içeren  **\<ayarı >** uygulamayı kullanmakta olduğu kullanıcı için özel etiketler. Öznitelikleri tanımlar.

## <a name="setting-element"></a>\<Ayarlama > öğesi

Bu öğe bir ayar tanımlar. Aşağıdaki özniteliklere sahiptir.

| Öznitelik        | Açıklama |
| ---------------- | ----------- |
| **adı**         | Gerekli. Ayar benzersiz kimliği. Visual Studio oluşturulan ayarları adıyla kaydedilir `ProjectName.Properties.Settings`. |
| **serializedAs** | Gerekli. Metin değeri serileştirmek için kullanılacak biçimi. Geçerli değerler şunlardır:<br><br>- `string`. Değer olarak dizesi kullanılarak serileştirilmiş bir <xref:System.ComponentModel.TypeConverter>.<br>- `xml`. Değer XML serileştirme kullanarak serileştirilir.<br>- `binary`. Değer ikili serileştirme kullanılarak metin ile kodlanmış ikili olarak serileştirilir.<br />- `custom`. Ayarlar sağlayıcısı serileştiren bilgiyi bu ayarın sahiptir ve XML'deki serileştirir. |

## <a name="value-element"></a>\<Değer > öğesi

Bu öğe bir ayarın değerini içerir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, iki uygulama kapsamlı ve iki kullanıcı kapsamlı ayarlarını tanımlayan uygulama ayarları dosyası gösterilmektedir:

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

[Uygulama ayarlarına genel bakış](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[Uygulama ayarları mimarisi](~/docs/framework/winforms/advanced/application-settings-architecture.md)
