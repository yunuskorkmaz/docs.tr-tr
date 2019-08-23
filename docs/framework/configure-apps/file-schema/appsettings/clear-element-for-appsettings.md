---
title: <appSettings> için <clear> öğesi
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 5d5da531bff3a0e9e198ba9b5ab6cf2b52bf36b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921307"
---
# <a name="clear-element-for-appsettings"></a>\<appSettings için \<> öğesi > Temizle

Özel uygulama ayarlarını temizler.

[ **\<Yapılandırma >** ](../configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<> Temizle**

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
