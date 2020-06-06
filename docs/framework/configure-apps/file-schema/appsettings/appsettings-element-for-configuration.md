---
title: <configuration> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
ms.openlocfilehash: ea341d562f4b163a3a1771da0f20903b7d64bcdf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155537"
---
# <a name="appsettings-element-for-configuration"></a>\<configuration> için \<appSettings> öğesi

Özel uygulama ayarlarını içerir. Bu, .NET Framework tarafından sunulan önceden tanımlanmış bir yapılandırma bölümüdür.

[**\<configuration>**](../configuration-element.md) &nbsp;&nbsp;**\<appSettings>**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **dosyasýný**  | İsteğe bağlı öznitelik.<br><br>Özel uygulama yapılandırma ayarlarını içeren bir dış dosyanın göreli yolunu belirtir. Belirtilen dosya,, ve öğelerinde belirtilen tür ayarları içerir **\<add>** **\<remove>** **\<clear>** ve bu öğelerle aynı anahtar/değer çifti biçimini kullanır.<br><br>Belirtilen yol, ana yapılandırma dosyasına göredir. Windows Forms bir uygulama için, bu, uygulama yapılandırma dosyasının konumunu değil, ikili klasördür (örneğin, */bin/Debug*). Web Forms uygulamalar için yol, *Web. config* dosyasının bulunduğu uygulama köküne göredir.<br><br>Belirtilen dosya bulunamazsa çalışma zamanı özniteliği yoksayar. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<configuration>** Dosyalarında](../configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<add>**](add-element-for-appsettings.md) | Özel bir uygulama ayarı ekler. |
| [**\<clear>**](clear-element-for-appsettings.md) | Önceden tanımlanmış tüm uygulama ayarlarını temizler. |
| [**\<remove>**](remove-element-for-appsettings.md) | Önceden tanımlanmış bir uygulama ayarını kaldırır. |

## <a name="remarks"></a>Açıklamalar

**\<appSettings>** Öğesi, veritabanı bağlantı dizeleri, dosya yolları, XML Web hizmeti URL 'leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama yapılandırma bilgilerini depolar. Öğesinde belirtilen anahtar/değer çiftlerine **\<appSettings>** sınıfı kullanılarak kodda erişilir <xref:System.Configuration.ConfigurationSettings> .

**file** **\<appSettings>** *Web. config* ve uygulama yapılandırma dosyalarının öğesinde dosya özniteliğini kullanabilirsiniz. Bu öznitelik, ek ayarlar sağlayan veya öğesinde belirtilen ayarları geçersiz kılan bir yapılandırma dosyasını belirtir **\<appSettings>** . **Dosya** özniteliği, bir Kullanıcı bir uygulama yapılandırma dosyasında belirtilen proje ayarlarını geçersiz kılmak istediğinde olduğu gibi, kaynak denetimi takım geliştirme senaryolarında kullanılabilir.

**Dosya** özniteliği tarafından belirtilen yapılandırma dosyaları yerine kök düğümüne sahip olmalıdır **\<appSettings>** **\<configuration>** .

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

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında (*Machine. config*) ve uygulama dizini düzeyinde olmayan *Web. config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](../index.md)
