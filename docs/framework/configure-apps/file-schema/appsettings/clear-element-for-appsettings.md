---
title: <appSettings> için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d321f3169344e9aa40d65b1722a533549de5315a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088732"
---
# <a name="clear-element-for-appsettings"></a>\<appSettings için > öğesi \<temizleyin >

Özel uygulama ayarlarını temizler.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<temizle >**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>Öznitelikler

Yok.

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Dosya yolları, XML Web hizmeti URL 'Leri veya diğer özel uygulama yapılandırma bilgileri gibi özel uygulama ayarlarını içerir. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel yapılandırma ayarlarının nasıl temizyükleneceğini göstermektedir:

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](../index.md)
