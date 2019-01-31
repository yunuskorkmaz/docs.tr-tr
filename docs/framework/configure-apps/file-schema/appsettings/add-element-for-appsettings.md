---
title: <add> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dde773dc722cf75da9d922ccf28af4bf4a09636c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277478"
---
# <a name="add-element-for-appsettings"></a>\<Ekle > öğesi için \<appSettings >

Özel uygulama ayarı ekler.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>Öznitelikler

|           | Açıklama |
| --------- | ----------- |
| **anahtar**   | Gerekli öznitelik.<br><br>Eklenecek anahtar adını belirtir. |
| **value** | Gerekli öznitelik.<br><br>Eklenecek anahtar değerini belirtir. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Dosya yolları, XML Web hizmeti URL'leri ya da bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama ayarları içerir. |

## <a name="child-elements"></a>Alt öğeleri

Hiçbiri

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir uygulamanın adı için özel yapılandırma ayarı eklemek gösterilmektedir:

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

Aşağıdaki örnekte `<add>` bir ASP.NET uygulamasında iki uyumluluk ayarlarını tanımlamak için:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
