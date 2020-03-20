---
title: <configuration> için <assemblyBinding> öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding
helpviewer_keywords:
- assemblyBinding Element
- <assemblyBinding> Element
ms.assetid: 6cc55983-b894-449b-8e26-b258e53939cd
ms.openlocfilehash: 21cf5e749b0dae310c3326f8abf82c6678fc97e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155485"
---
# <a name="assemblybinding-element-for-configuration"></a>\<derlemeYapılandırma> \<için> öğesi bağlama

Yapılandırma düzeyinde derleme bağlama ilkesini belirtir.

yapılandırma &nbsp; &nbsp;>[** \<**](configuration-element.md) ** \<montajBağlayıcı>**

## <a name="syntax"></a>Sözdizimi

```xml
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
  <!-- Configuration files to include. -->
</assemblyBinding>
```

## <a name="attribute"></a>Öznitelik

|           | Açıklama |
| --------- | ----------- |
| **Xmlns** | Gerekli öznitelik.<br><br>Derleme bağlama için gereken XML ad alanını belirtir. Değer olarak "urn:schemas-microsoft-com:asm.v1" dizesini kullanın. |

## <a name="parent-element"></a>Üst öğe

|     | Açıklama |
| --- | ----------- |
| [**\<yapılandırma>**](configuration-element.md) | Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe. |

## <a name="child-element"></a>Alt öğe

|     | Açıklama |
| --- | ----------- |
| [**\<linkedConfiguration>**](linkedconfiguration-element.md) | İçerecek bir yapılandırma dosyası belirtir. |

## <a name="remarks"></a>Açıklamalar

LinkedConfiguration>öğesi, uygulama yapılandırma dosyalarının derleme yapılandırma ayarlarını çoğaltmak yerine iyi bilinen konumlarda derleme yapılandırma dosyalarını içermesi için izin vererek bileşen derlemelerinin yönetimini kolaylaştırır. [** \<**](linkedconfiguration-element.md)

> [!NOTE]
> ** \<Bağlantılı Yapılandırma>** öğesi, Windows yan yana bildirimleri olan uygulamalar için desteklenmez.

## <a name="example"></a>Örnek

Aşağıdaki örnek, yerel sabit diske yapılandırma dosyasının nasıl eklenmeygerektiğini gösterir:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml" />
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework için yapılandırma dosyası şeması](index.md)
