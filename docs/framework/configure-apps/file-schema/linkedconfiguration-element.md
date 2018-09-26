---
title: '&lt;linkedConfiguration&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
author: mcleblanc
ms.author: markl
ms.openlocfilehash: c5186aa94993ba551252db6fef55853b5b554789
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170827"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > öğesi

Dahil edilecek bir yapılandırma dosyası belirtir.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<assemblyBinding >**](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration >**

## <a name="syntax"></a>Sözdizimi

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **href**  | Gerekli öznitelik.<br><br>Dahil etmek için yapılandırma dosyasının URL'si. Desteklenen tek biçimi **href** özniteliği `file://`. Yerel dosyaları ve UNC dosyaları desteklenir. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<assemblyBinding >** öğesi](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Derleme bağlama ilkesini yapılandırma düzeyinde belirtir. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

**\<LinkedConfiguration >** öğesi bileşeni derlemeler için bakım basitleştirir. İyi bilinen bir konumda bulunan bir yapılandırma dosyası bir derleme bir veya daha fazla kullanmanız durumunda derleme kullanan uygulamaların yapılandırma dosyalarını kullanabilirler  **\<linkedConfiguration >** yapılandırma bilgilerini doğrudan dahil olmak üzere yerine derleme yapılandırma dosyası eklenecek öğe. Bileşen derlemesi değiştiğinde, ortak yapılandırma dosyasını güncelleştirme derleme kullanan tüm uygulamalar için güncelleştirilmiş yapılandırma bilgilerini sağlar.

> [!NOTE]
> **\<LinkedConfiguration >** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.

Aşağıdaki kuralları bağlantılı yapılandırma dosyaları yöneten:

- Dahil edilen yapılandırma dosyalarındaki ayarlar yalnızca yükleyici bağlama ilkesi etkiler ve yalnızca yükleyicisi tarafından kullanılır. Dahil edilen yapılandırma dosyalarını ayarları ilkeleri bağlama dışında olabilir, ancak bu ayarlar, herhangi bir etkisi yok.

- Desteklenen tek biçimi `href` özniteliği `file://`. Yerel dosyaları ve UNC dosyaları desteklenir.

- Yapılandırma dosyası başına bağlı yapılandırmaları sayısı hiçbir kısıtlama yoktur.

- Tüm bağlantılı yapılandırma dosyaları davranıştır benzer bir dosya oluşturmak üzere birleştirilir `#include` C/C++'ta yönergesi.

- **\<LinkedConfiguration >** öğesi yalnızca uygulama yapılandırma dosyalarında izin verilir; içindeki sayılır *Machine.config*.

- Döngüsel başvuru algılandı ve sonlandırıldı. Diğer bir deyişle,  **\<linkedConfiguration >** yapılandırma dosyalarını bir dizi öğeleri formunda bir döngü, döngü algılandı ve durduruldu.

## <a name="example"></a>Örnek

Aşağıdaki örnek yapılandırma dosyasını yerel sabit diskten nasıl ekleyeceğinizi gösterir:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

[**\<assemblyBinding >** öğesi](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
[.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
