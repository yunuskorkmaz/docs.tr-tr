---
title: <linkedConfiguration> öğesi
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
ms.openlocfilehash: 14ee2275ecf690ab16ffaabd71fbbe7e1a4897bc
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087959"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration > öğesi

Dahil edilecek bir yapılandırma dosyasını belirtir.

[ **\<configuration >** ](configuration-element.md) \
&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration >**

## <a name="syntax"></a>Sözdizimi

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **değerini**  | Gerekli öznitelik.<br><br>Dahil edilecek yapılandırma dosyasının URL 'SI. **Href** özniteliği için desteklenen tek Biçim `file://`. Yerel dosyalar ve UNC dosyaları desteklenir. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**assemblyBinding >\<** Dosyalarında](assemblybinding-element-for-configuration.md) | Yapılandırma düzeyinde derleme bağlama ilkesini belirtir. |

## <a name="child-elements"></a>Alt öğeleri

Yok.

## <a name="remarks"></a>Açıklamalar

**\<LinkedConfiguration>** öğesi bileşeni derlemeler için bakım basitleştirir. Bir veya daha fazla uygulama, iyi bilinen bir konumda bulunan bir yapılandırma dosyası olan bir derlemeyi kullanıyorsa, derlemeyi kullanan uygulamaların yapılandırma dosyaları, yapılandırma bilgilerini doğrudan dahil etmek yerine, derleme yapılandırma dosyasını dahil etmek için **\<linkedconfiguration >** öğesini kullanabilir. Bileşen derlemesine hizmet verilirken, ortak yapılandırma dosyasını güncelleştirme, derlemeyi kullanan tüm uygulamalara güncelleştirilmiş yapılandırma bilgileri sağlar.

> [!NOTE]
> **\<LinkedConfiguration>** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.

Aşağıdaki kurallar, bağlantılı yapılandırma dosyalarının kullanımını yönetir:

- Dahil edilen yapılandırma dosyalarındaki ayarlar yalnızca yükleyici bağlama ilkesini etkiler ve yalnızca yükleyici tarafından kullanılır. Dahil edilen yapılandırma dosyaları, bağlama ilkeleri dışında ayarları olabilir, ancak bu ayarların hiçbir etkisi yoktur.

- `href` özniteliği için desteklenen tek Biçim `file://`. Yerel dosyalar ve UNC dosyaları desteklenir.

- Yapılandırma dosyası başına bağlı yapılandırma sayısında kısıtlama yoktur.

- Tüm bağlantılı yapılandırma dosyaları, C/C++içindeki `#include` yönergesinin davranışına benzer şekilde tek bir dosya oluşturacak şekilde birleştirilir.

- **\<LinkedConfiguration>** öğesi yalnızca uygulama yapılandırma dosyalarında izin verilir; içindeki sayılır *Machine.config*.

- Döngüsel başvurular algılanır ve sonlandırılır. Diğer bir deyişle, bir dizi yapılandırma dosyası için **\<linkedconfiguration >** öğeleri bir döngü oluşturuyor ise döngü algılanır ve durdurulur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, yerel sabit diskten yapılandırma dosyasının nasıl ekleneceğini gösterir:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [**assemblyBinding >\<** Dosyalarında](assemblybinding-element-for-configuration.md)
- [.NET Framework için yapılandırma dosyası şeması](index.md)
