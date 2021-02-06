---
description: 'İçin: öğesi hakkında daha fazla bilgi <add><appSettings>'
title: <appSettings> için <add> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: f10ffe517b3b25543bc7baed0c7d2af13f48ab02
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652893"
---
# <a name="add-element-for-appsettings"></a>\<appSettings> için \<add> öğesi

Özel bir uygulama ayarı ekler.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a>Syntax

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>Öznitelikler

|           | Description |
| --------- | ----------- |
| **anahtar**   | Gerekli öznitelik.<br><br>Eklenecek anahtarın adını belirtir. |
| **değer** | Gerekli öznitelik.<br><br>Eklenecek anahtarın değerini belirtir. |

## <a name="parent-element"></a>Üst öğe

|     | Description |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir. |

## <a name="child-elements"></a>Alt öğeleri

Hiçbiri

## <a name="example"></a>Örnek

Aşağıdaki örnek, uygulamanın adı için nasıl özel bir yapılandırma ayarı ekleneceğini gösterir:

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

Aşağıdaki örnek, `<add>` bir ASP.NET uygulamasında iki uyumluluk ayarı tanımlamak için öğesini kullanır:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](../index.md)
