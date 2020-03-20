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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155537"
---
# <a name="appsettings-element-for-configuration"></a>\<yapılandırma> için \<> öğesi

Özel uygulama ayarları içerir. Bu, .NET Framework tarafından sağlanan önceden tanımlanmış bir yapılandırma bölümüdür.

yapılandırma &nbsp; &nbsp;>[** \<**](../configuration-element.md) ** \<appAyarlar>**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <!-- Elements to add, clear, or remove configuration settings -->
</appSettings>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **Dosya**  | İsteğe bağlı öznitelik.<br><br>Özel uygulama yapılandırma ayarları içeren harici bir dosyaya göreli bir yol belirtir. Belirtilen dosya, ** \<>ekleme, ** ** \<>kaldırma **ve ** \<>öğelerini temizleme** de belirtilen ayarların aynı türünü içerir ve bu öğelerle aynı anahtar/değer çifti biçimini kullanır.<br><br>Belirtilen yol ana yapılandırma dosyasına göredir. Windows Forms uygulaması için bu ikili klasördür *(//bin/hata ayıklama*gibi), uygulama yapılandırma dosyasının konumu değildir. Web Formları uygulamaları için yol, *web.config* dosyasının bulunduğu uygulama köküne göredir.<br><br>Belirtilen dosya bulunamazsa çalışma süresi özniteliği yok sayar. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [** \<yapılandırma>** Öğe](../configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-elements"></a>Alt öğeleri

|     | Açıklama |
| --- | ----------- |
| [**\<>ekleyin**](add-element-for-appsettings.md) | Özel bir uygulama ayarı ekler. |
| [**\<açık>**](clear-element-for-appsettings.md) | Daha önce tanımlanmış tüm uygulama ayarlarını temizler. |
| [**\<>kaldırmak**](remove-element-for-appsettings.md) | Daha önce tanımlanmış bir uygulama ayarını kaldırır. |

## <a name="remarks"></a>Açıklamalar

AppSettings>öğesi veritabanı bağlantı dizeleri, dosya yolları, XML Web hizmeti URL'leri veya bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama yapılandırma bilgilerini depolar. ** \<** ** \<Uygulama Ayarları>** öğesinde belirtilen anahtar/değer çiftleri <xref:System.Configuration.ConfigurationSettings> sınıf kullanılarak kod olarak erişilir.

*Web.config* ve uygulama yapılandırma dosyalarının ** \<appSettings>** öğesinde **dosya** özniteliğini kullanabilirsiniz. Bu öznitelik, ek ayarlar sağlayan veya ** \<uygulama Ayarları>** öğesinde belirtilen ayarları geçersiz kılan bir yapılandırma dosyası belirtir. **Dosya** özniteliği, kullanıcının bir uygulama yapılandırma dosyasında belirtilen proje ayarlarını geçersiz kılmak istemesi gibi kaynak denetimi ekibi geliştirme senaryolarında kullanılabilir.

**Dosya** özniteliği tarafından belirtilen yapılandırma dosyaları, ** \<yapılandırma>** yerine ** \<>appSettings** kök düğümüne sahip olmalıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel bir uygulama ayarı tanımlayan harici bir uygulama ayarları dosyasını *(custom.config)* gösterir:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Aşağıdaki örnek, dış ayarlar dosyasındaki ayarı tüketen ve kendi uygulama ayarını ayarlayan bir uygulama yapılandırma dosyasını gösterir:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında, makine yapılandırma dosyasında *(Machine.config)* ve uygulama dizini düzeyinde olmayan *Web.config* dosyalarında kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](../index.md)
