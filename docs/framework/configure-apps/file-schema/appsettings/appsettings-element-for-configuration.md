---
title: <appSettings> için <configuration> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings
helpviewer_keywords:
- appSettings Element
- <appSettings> Element
ms.assetid: 39694cc4-6b84-45a6-9329-385a0d8b48fe
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6112d87afcca8b2f54508d03d3ea4c0781d7e475
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119277"
---
# <a name="appsettings-element-for-configuration"></a>\<yapılandırması için \<appSettings > öğesi >

Özel uygulama ayarlarını içerir. Bu, .NET Framework tarafından sunulan önceden tanımlanmış bir yapılandırma bölümüdür.

[ **\<yapılandırma >** ](../configuration-element.md)   
&nbsp;&nbsp; **\<appSettings >**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **dosyasýný**  | İsteğe bağlı öznitelik.<br><br>Özel uygulama yapılandırma ayarlarını içeren bir dış dosyanın göreli yolunu belirtir. Belirtilen dosya **\<> eklemek**, **> kaldırmak\<** ve\<**Temizle >** öğelerini ve bu öğelerle aynı anahtar/değer çifti biçimini kullanır.<br><br>Belirtilen yol, ana yapılandırma dosyasına göredir. Windows Forms bir uygulama için, bu, uygulama yapılandırma dosyasının konumunu değil, ikili klasördür (örneğin, */bin/Debug*). Web Forms uygulamalar için yol, *Web. config* dosyasının bulunduğu uygulama köküne göredir.<br><br>Belirtilen dosya bulunamazsa çalışma zamanının özniteliği yoksaydığına unutmayın. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<yapılandırma >** Dosyalarında](../configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [ **\<> Ekle**](add-element-for-appsettings.md) | Özel bir uygulama ayarı ekler. |
| [ **\<Temizle >** ](clear-element-for-appsettings.md) | Önceden tanımlanmış tüm uygulama ayarlarını temizler. |
| [ **\<> Kaldır**](remove-element-for-appsettings.md) | Önceden tanımlanmış bir uygulama ayarını kaldırır. |

## <a name="remarks"></a>Açıklamalar

**\<AppSettings >** öğesi veritabanı bağlantı dizeleri, dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgileri için gibi özel bir uygulama yapılandırma bilgilerini depolayan bir uygulama. **\<appSettings >** öğesinde belirtilen anahtar/değer çiftlerine <xref:System.Configuration.ConfigurationSettings> sınıfı kullanılarak kodla erişilir.

*Web. config* ve uygulama yapılandırma dosyalarının **\<appSettings >** öğesinde **Dosya** özniteliğini kullanabilirsiniz. Bu öznitelik, ek ayarlar sağlayan veya **\<appSettings >** öğesinde belirtilen ayarları geçersiz kılan bir yapılandırma dosyasını belirtir. **Dosya** özniteliği, bir Kullanıcı bir uygulama yapılandırma dosyasında belirtilen proje ayarlarını geçersiz kılmak istediğinde olduğu gibi, kaynak denetimi takım geliştirme senaryolarında kullanılabilir.

Yapılandırma dosyaları tarafından belirtilen **dosya** öznitelik, bir kök düğümü olmalıdır **\<appSettings >** yerine **\<yapılandırma >** .

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
