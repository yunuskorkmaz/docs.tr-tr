---
title: Uygulama Ayarları şema
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242835"
---
# <a name="application-settings-schema"></a>Uygulama Ayarları şema

Uygulama ayarları, windows formları veya ASP.NET uygulamasının uygulama kapsamı ve kullanıcı kapsamı namına ayarları depolamasına ve almasına olanak tanır. Bu bağlamda, *ayar,* uygulamaya özgü veya geçerli kullanıcıya özgü olabilecek herhangi bir bilgi parçasıdır — veritabanı bağlantı dizesinden kullanıcının tercih edilen varsayılan pencere boyutuna kadar her şey.

Varsayılan olarak, Windows Forms uygulamasındaki <xref:System.Configuration.LocalFileSettingsProvider> uygulama ayarları, bir XML yapılandırma dosyasında ayarları depolamak için .NET yapılandırma sistemini kullanan sınıfı kullanır. Uygulama ayarları tarafından kullanılan dosyalar hakkında daha fazla bilgi için [Uygulama Ayarları Mimarisi'ne](../../winforms/advanced/application-settings-architecture.md)bakın.

Uygulama ayarları, kullandığı yapılandırma dosyalarının bir parçası olarak aşağıdaki öğeleri tanımlar.

| Öğe                    | Açıklama                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationAyarlar>** | Uygulamaya ** \<** özgü tüm ayar>etiketleri içerir.                         |
| **\<userAyarlar>**        | Geçerli ** \<kullanıcıya** özgü tüm ayarları>etiketleri içerir.                        |
| **\<>ayarlama**             | Bir ayar tanımlar. Uygulamanın alt>** \<veya** ** \<kullanıcıAyarlar>. ** |
| **\<değer>**               | Ayarın değerini tanımlar. >** \<ayar **Çocuk .                                   |

## <a name="applicationsettings-element"></a>\<applicationAyarlar> öğesi

Bu öğe, ** \<** istemci bilgisayarda uygulamanın bir örneğine özgü tüm ayar>etiketleri içerir. Hiçbir öznitelik tanımlar.

## <a name="usersettings-element"></a>\<userAyarlar> öğesi

Bu öğe, ** \<** uygulamayı şu anda kullanmakta olan kullanıcıya özgü tüm ayar>etiketleri içerir. Hiçbir öznitelik tanımlar.

## <a name="setting-element"></a>\<> öğesi ayarlama

Bu öğe bir ayar tanımlar. Aşağıdaki özelliklere sahiptir.

| Öznitelik        | Açıklama |
| ---------------- | ----------- |
| **Adı**         | Gereklidir. Ayarın benzersiz kimliği. Visual Studio aracılığıyla oluşturulan ayarlar `ProjectName.Properties.Settings`adıyla kaydedilir. |
| **serializeAs** | Gereklidir. Metne değeri serihale getirmek için kullanılacak biçim. Geçerli değerler:<br><br>- `string`. Değer bir dize olarak serihale edilir. <xref:System.ComponentModel.TypeConverter><br>- `xml`. Değer XML serileştirme kullanılarak seri hale getirilir.<br>- `binary`. Değer, ikili serileştirme kullanılarak metin kodlu ikili olarak serihale edilir.<br />- `custom`. Ayarlar sağlayıcısı bu ayarı doğal bilgiye sahiptir ve serihale eder ve de-serializes. |

## <a name="value-element"></a>\<değer> öğesi

Bu öğe bir ayarın değerini içerir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, uygulama kapsamı içinde iki ayar ve iki kullanıcı kapsamı ayarı tanımlayan bir uygulama ayarları dosyası gösterilmektedir:

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
