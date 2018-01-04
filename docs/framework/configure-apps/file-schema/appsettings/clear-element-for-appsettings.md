---
title: "&lt;Clear&gt; öğesi için &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54479cab9abc2c1a107cd055341404c0fe1308fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clear-element-for-appsettings"></a>\<Clear > öğesi için \<appSettings >

Özel uygulama ayarlarını temizler.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Clear >**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>Öznitelikler

Yok.

## <a name="parent-element"></a>Üst öğesi

|     | Açıklama |
| --- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Dosya yolları, XML Web hizmeti URL'leri veya başka bir özel uygulama yapılandırma bilgilerini gibi özel uygulama ayarlarını içerir. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel yapılandırma ayarlarına sıfırlamaya gösterilmektedir:

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>Ayrıca bkz.

[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
