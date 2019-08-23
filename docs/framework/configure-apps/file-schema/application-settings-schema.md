---
title: Uygulama ayarları şeması
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 89a08434332b0242fe57e9dcaa3b3ebcc5692d06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927757"
---
# <a name="application-settings-schema"></a>Uygulama ayarları şeması

Uygulama ayarları bir Windows Forms veya ASP.NET uygulamasının uygulama kapsamlı ve kullanıcı kapsamlı ayarları depolamasına ve almasına izin verir. Bu bağlamda, bir *ayar* , uygulamaya özgü veya geçerli kullanıcıya özgü olabilecek herhangi bir bilgi olan bir veritabanı bağlantı dizesinden kullanıcının tercih edilen varsayılan pencere boyutuna kadar her şey olabilir.

Varsayılan olarak, bir Windows Forms uygulamasındaki uygulama ayarları, ayarları bir <xref:System.Configuration.LocalFileSettingsProvider> XML yapılandırma dosyasında depolamak için .NET yapılandırma sistemini kullanan sınıfını kullanır. Uygulama ayarları tarafından kullanılan dosyalar hakkında daha fazla bilgi için bkz. [uygulama ayarları mimarisi](../../winforms/advanced/application-settings-architecture.md).

Uygulama ayarları, kullandığı yapılandırma dosyalarının bir parçası olarak aşağıdaki öğeleri tanımlar.

| Öğe                    | Açıklama                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | Uygulamaya özgü tüm  **\<ayar >** etiketlerini içerir.                         |
| **\<userSettings >**        | Geçerli kullanıcıya özgü tüm  **\<ayar >** etiketlerini içerir.                        |
| **\<> ayarlama**             | Bir ayarı tanımlar. **\<ApplicationSettings >** ya  **\<da UserSettings >** alt öğesi. |
| **\<value>**               | Bir ayarın değerini tanımlar. > Ayarının alt öğesi.  **\<**                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > öğesi

Bu öğe, bir istemci bilgisayarında uygulamanın bir örneğine özgü  **\<> Tüm ayarı** içerir. Hiçbir öznitelik tanımlamıyor.

## <a name="usersettings-element"></a>\<userSettings > öğesi

Bu öğe, şu anda uygulamayı kullanan kullanıcıya özgü tüm  **\<ayar > ayarlarını** içerir. Hiçbir öznitelik tanımlamıyor.

## <a name="setting-element"></a>\<> öğesi ayarlanıyor

Bu öğe bir ayar tanımlar. Aşağıdaki özniteliklere sahiptir.

| Öznitelik        | Açıklama |
| ---------------- | ----------- |
| **name**         | Gerekli. Ayarın benzersiz KIMLIĞI. Visual Studio ile oluşturulan ayarlar, adıyla `ProjectName.Properties.Settings`birlikte kaydedilir. |
| **serializedAs** | Gerekli. Değerin metin olarak serileştirilmesi için kullanılacak biçim. Geçerli değerler şunlardır:<br><br>- `string`. Değer, kullanarak <xref:System.ComponentModel.TypeConverter>bir dize olarak serileştirilir.<br>- `xml`. Değer XML serileştirme kullanılarak serileştirilir.<br>- `binary`. Değer, ikili serileştirme kullanılarak metin kodlu ikili olarak serileştirilir.<br />- `custom`. Ayarlar sağlayıcısı bu ayar hakkında bilgi sahibi ve serileştirildikleri ve serileştirildikleri. |

## <a name="value-element"></a>\<değer > öğesi

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

- [Uygulama Ayarlarına Genel Bakış](../../winforms/advanced/application-settings-overview.md)
- [Uygulama Ayarları Mimarisi](../../winforms/advanced/application-settings-architecture.md)
