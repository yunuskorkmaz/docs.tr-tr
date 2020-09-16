---
title: Uygulama ayarları şeması
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: fc9cd8ac3819c6a02019c871e7bd45ceb4c2cef7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90552316"
---
# <a name="application-settings-schema"></a>Uygulama ayarları şeması

Uygulama ayarları bir Windows Forms veya ASP.NET uygulamasının uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamasına ve almasına izin verir. Bu bağlamda, bir *ayar* , uygulamaya özgü veya geçerli kullanıcıya özgü olabilecek herhangi bir bilgi olan bir veritabanı bağlantı dizesinden kullanıcının tercih edilen varsayılan pencere boyutuna kadar her şey olabilir.

Varsayılan olarak, bir Windows Forms uygulamasındaki uygulama ayarları, <xref:System.Configuration.LocalFileSettingsProvider> ayarları BIR XML yapılandırma dosyasında depolamak için .NET yapılandırma sistemini kullanan sınıfını kullanır. Uygulama ayarları tarafından kullanılan dosyalar hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](/dotnet/desktop/winforms/advanced/application-settings-architecture).

Uygulama ayarları, kullandığı yapılandırma dosyalarının bir parçası olarak aşağıdaki öğeleri tanımlar.

| Öğe                    | Açıklama                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | **\<setting>** Uygulamaya özgü tüm etiketleri içerir.                         |
| **\<userSettings>**        | **\<setting>** Geçerli kullanıcıya özgü tüm etiketleri içerir.                        |
| **\<setting>**             | Bir ayarı tanımlar. Ya da alt **\<applicationSettings>** öğesi **\<userSettings>** . |
| **\<value>**               | Bir ayarın değerini tanımlar. Alt öğesi **\<setting>** .                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings> öğesi

Bu öğe **\<setting>** , bir istemci bilgisayarındaki uygulamanın bir örneğine özgü olan tüm etiketleri içerir. Hiçbir öznitelik tanımlamıyor.

## <a name="usersettings-element"></a>\<userSettings> öğesi

Bu öğe, **\<setting>** Şu anda uygulamayı kullanan kullanıcıya özgü tüm etiketleri içerir. Hiçbir öznitelik tanımlamıyor.

## <a name="setting-element"></a>\<setting> öğesi

Bu öğe bir ayar tanımlar. Aşağıdaki özniteliklere sahiptir.

| Öznitelik        | Açıklama |
| ---------------- | ----------- |
| **ada**         | Gereklidir. Ayarın benzersiz KIMLIĞI. Visual Studio ile oluşturulan ayarlar, adıyla birlikte kaydedilir `ProjectName.Properties.Settings` . |
| **serializeAs** | Gereklidir. Değerin metin olarak serileştirilmesi için kullanılacak biçim. Geçerli değerler:<br><br>- `string`. Değer, kullanarak bir dize olarak serileştirilir <xref:System.ComponentModel.TypeConverter> .<br>- `xml`. Değer XML serileştirme kullanılarak serileştirilir.<br>- `binary`. Değer, ikili serileştirme kullanılarak metin kodlu ikili olarak serileştirilir.<br />- `custom`. Ayarlar sağlayıcısı bu ayar hakkında bilgi sahibi ve serileştirildikleri ve serileştirildikleri. |

## <a name="value-element"></a>\<value> öğesi

Bu öğe bir ayarın değerini içerir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, uygulama kapsamlı iki ayarı ve kullanıcı kapsamlı iki ayarı tanımlayan bir uygulama ayarları dosyası gösterir:

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

- [Uygulama Ayarlarına Genel Bakış](/dotnet/desktop/winforms/advanced/application-settings-overview)
- [Uygulama Ayarları Mimarisi](/dotnet/desktop/winforms/advanced/application-settings-architecture)
