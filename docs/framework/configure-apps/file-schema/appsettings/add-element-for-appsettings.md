---
title: "&lt;ekleme&gt; öğesi için &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d080a7c63ddda0577e66d2e7ddd433c7fd5fdbd1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="add-element-for-appsettings"></a>\<Ekle > öğesi için \<appSettings >

Özel uygulama ayarı ekler.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<ekleme >**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>Öznitelikler

|           | Açıklama |
| --------- | ----------- |
| **anahtarı**   | Gerekli öznitelik.<br><br>Eklenecek anahtar adını belirtir. |
| **value** | Gerekli öznitelik.<br><br>Eklenecek anahtar değerini belirtir. |

## <a name="parent-element"></a>Üst öğesi

|     | Açıklama |
| --- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Dosya yolları, XML Web hizmeti URL'leri veya diğer özel yapılandırma bilgilerini bir uygulama gibi özel uygulama ayarlarını içerir. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="example"></a>Örnek

Aşağıdaki örnekte uygulamanın adı için bir özel yapılandırma ayarı ekleme gösterir:

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
