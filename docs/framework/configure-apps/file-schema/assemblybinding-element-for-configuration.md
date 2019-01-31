---
title: <assemblyBinding> için <configuration> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: f5992a6085c32d37f56319cf8b2c361542c441e7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257345"
---
# <a name="assemblybinding-element-for-configuration"></a>\<assemblyBinding > öğesi için \<yapılandırma >

Derleme bağlama ilkesini yapılandırma düzeyinde belirtir.

[**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<assemblyBinding >**

## <a name="syntax"></a>Sözdizimi

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **xmlns** | Gerekli öznitelik.<br><br>Derleme bağlama için gerekli XML ad alanı belirtir. Use the string "urn:schemas-microsoft-com:asm.v1" as the value. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<Yapılandırma >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-element"></a>Alt öğe

|     | Açıklama |
| --- | ----------- |
| [**\<linkedConfiguration >**](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) | Dahil edilecek bir yapılandırma dosyası belirtir. |

## <a name="remarks"></a>Açıklamalar

[  **\<LinkedConfiguration >** ](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) öğesi yapılandırma dosyalarında derlemeyi dahil etmek için uygulama yapılandırma dosyaları vererek bileşen derlemelerini yönetimini basitleştirir iyi bilinen konumları, çoğaltma derleme yapılandırma ayarları yerine.

> [!NOTE]
>  **\<LinkedConfiguration >** öğesi Windows yan yana bildirimleri olan uygulamalar için desteklenmez.

## <a name="example"></a>Örnek

Aşağıdaki örnek bir yapılandırma dosyasını yerel sabit diskte nasıl ekleyeceğinizi gösterir:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework yapılandırma dosyası şeması](~/docs/framework/configure-apps/file-schema/index.md)
