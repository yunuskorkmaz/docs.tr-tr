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
manager: markl
ms.openlocfilehash: 71769efa1233fc8a693219dc02ae56ea39c164e7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > öğesi

Dahil etmek için bir yapılandırma dosyası belirtir.

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
| **href**  | Gerekli öznitelik.<br><br>Dahil etmek için yapılandırma dosyası URL'si. İçin desteklenen tek biçimi **href** özniteliği `file://`. Yerel dosyaları ve UNC dosyaları desteklenir. |

## <a name="parent-element"></a>Üst öğesi

|     | Açıklama |
| --- | ----------- |
| [**\<assemblyBinding >** öğesi](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | Derleme bağlama ilkesi yapılandırma düzeyinde belirtir. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

**\<LinkedConfiguration >** öğesi basitleştirir bileşen derlemeleri için bakım. Bir veya daha fazla uygulama iyi bilinen bir konumda bulunan bir yapılandırma dosyası sahip bir derleme kullanıyorsanız, derleme kullanan uygulamalar, yapılandırma dosyalarını kullanabilirsiniz  **\<linkedConfiguration >** yapılandırma bilgilerini doğrudan da dahil olmak üzere yerine derleme yapılandırma dosyası eklenecek öğe. Bileşen derleme hizmet, ortak yapılandırma dosyasını güncelleştirme derleme kullanan tüm uygulamalar için güncelleştirilmiş yapılandırma bilgileri sağlar.

> [!NOTE]
> **\<LinkedConfiguration >** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.

Aşağıdaki kuralları bağlantılı yapılandırma dosyaları kullanımını yöneten:

- Dahil edilen yapılandırma dosyalarında ayarlar yalnızca yükleyicisi bağlama ilkesi etkileyebilir ve yalnızca yükleyicisi tarafından kullanılır. Dahil edilen yapılandırma dosyalarını ilkeleri bağlama farklı ayarlara sahip olabilir, ancak bu ayarları herhangi bir etkisi yoktur.

- İçin desteklenen tek biçimi `href` özniteliği `file://`. Yerel dosyaları ve UNC dosyaları desteklenir.

- Yapılandırma dosya başına bağlı yapılandırmalar sayısı hiçbir kısıtlama yoktur.

- Tüm bağlantılı yapılandırma dosyaları için davranışını benzer bir dosyayı oluşturmak için birleştirilir `#include` C/c++ yönergesi.

- **\<LinkedConfiguration >** yalnızca uygulama yapılandırma dosyaları öğesine izin verilir; içinde göz ardı *Machine.config*.

- Döngüsel başvuru algılandı ve sonlandırıldı. Diğer bir deyişle,  **\<linkedConfiguration >** yapılandırma dosyalarını bir dizi öğeleri formunda bir döngü, döngü algılandı ve durduruldu.

## <a name="example"></a>Örnek

Aşağıdaki örnek, yerel sabit disk yapılandırma dosyasından dahil gösterilmektedir:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

[**\<assemblyBinding >** öğesi](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md)   
[.NET Framework için yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
