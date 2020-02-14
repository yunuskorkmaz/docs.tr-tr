---
title: <remove> için <appSettings> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215487"
---
# <a name="remove-element-for-appsettings"></a>\<appSettings için > öğesini \<kaldırın >

Özel uygulama ayarlarını kaldırır.

[ **\<yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<kaldır >**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>Öznitelik

|         | Açıklama |
| ------- | ----------- |
| **anahtar** | Gerekli öznitelik.<br><br>Kaldırılacak anahtarın adını belirtir. |

### <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Dosya yolları, XML Web hizmeti URL 'Leri veya bir uygulama için başka özel yapılandırma bilgileri gibi özel uygulama ayarlarını içerir. |

## <a name="child-elements"></a>Alt öğeleri

Hiçbiri

## <a name="example"></a>Örnek

Aşağıdaki örnek, `ApplicationName`için özel bir yapılandırma ayarının nasıl kaldırılacağını gösterir:

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](../index.md)
