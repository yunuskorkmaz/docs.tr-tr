---
title: <configuration> için <assemblyBinding> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: e0b83c4b3573ab6819654e72cac1bf3e4a0ba637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921270"
---
# <a name="assemblybinding-element-for-configuration"></a>\<Yapılandırma > için \<assemblyBinding > öğesi

Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.

[ **\<Yapılandırma >** ](configuration-element.md)   
&nbsp;&nbsp; **\<assemblyBinding >**

## <a name="syntax"></a>Sözdizimi

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **özniteliði** | Gerekli öznitelik.<br><br>Derleme bağlaması için gereken XML ad alanını belirtir. Değer olarak "urn: schemas-microsoft-com: asm. v1" dizesini kullanın. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<Yapılandırma >** ](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-element"></a>Alt öğe

|     | Açıklama |
| --- | ----------- |
| [ **\<linkedConfiguration>** ](linkedconfiguration-element.md) | Dahil edilecek bir yapılandırma dosyasını belirtir. |

## <a name="remarks"></a>Açıklamalar

[ **\<LinkedConfiguration>** ](linkedconfiguration-element.md) öğesi yapılandırma dosyalarında derlemeyi dahil etmek için uygulama yapılandırma dosyaları vererek bileşen derlemelerini yönetimini basitleştirir iyi bilinen konumları, çoğaltma derleme yapılandırma ayarları yerine.

> [!NOTE]
> **\<LinkedConfiguration>** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.

## <a name="example"></a>Örnek

Aşağıdaki örnek, yerel sabit diske bir yapılandırma dosyasının nasıl ekleneceğini göstermektedir:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
