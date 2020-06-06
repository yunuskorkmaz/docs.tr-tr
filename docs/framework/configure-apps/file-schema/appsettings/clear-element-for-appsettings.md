---
title: <appSettings> için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 266d32ccb8b322f0472e0f552f9c0fc877c9a78e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214790"
---
# <a name="clear-element-for-appsettings"></a>\<appSettings> için \<clear> öğesi

Özel uygulama ayarlarını temizler.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>Sözdizimi

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>Öznitelikler

Yok

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | Dosya yolları, XML Web hizmeti URL 'Leri veya diğer özel uygulama yapılandırma bilgileri gibi özel uygulama ayarlarını içerir. |

## <a name="child-elements"></a>Alt öğeleri

Yok

## <a name="example"></a>Örnek

Aşağıdaki örnek, özel yapılandırma ayarlarının nasıl temizyükleneceğini göstermektedir:

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](../index.md)
