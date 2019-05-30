---
title: <appSettings> için <remove> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 62913face910ae9500aa5e6f2f443db67ffd4240
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301274"
---
# <a name="remove-element-for-appsettings"></a>\<kaldırma > öğesi için \<appSettings >

Özel uygulama ayarları kaldırır.

[ **\<Yapılandırma >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<kaldırma >**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>Öznitelik

|         | Açıklama |
| ------- | ----------- |
| **anahtar** | Gerekli öznitelik.<br><br>Kaldırılacak anahtar adını belirtir. |

### <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<appSettings >** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Dosya yolları, XML Web hizmeti URL'leri ya da bir uygulama için diğer özel yapılandırma bilgileri gibi özel uygulama ayarları içerir. |

## <a name="child-elements"></a>Alt öğeleri

None

## <a name="example"></a>Örnek

Aşağıdaki örnek bir özel yapılandırma ayarını kaldırın gösterilmiştir `ApplicationName`:

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
