---
title: Windows Forms Yapılandırma Bölümü
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151838"
---
# <a name="windows-forms-configuration-section"></a>Windows Forms Yapılandırma Bölümü
Windows Forms yapılandırma ayarları, Windows Forms uygulamanın çok Monitor desteği, yüksek DPı desteği ve diğer önceden tanımlanmış yapılandırma ayarları gibi özelleştirilmiş uygulama ayarları hakkında bilgi depolamasına ve almasına izin verir.

Windows Forms uygulama yapılandırma ayarları bir uygulama yapılandırma dosyasının `System.Windows.Forms.ApplicationConfigurationSection` öğesinde saklanır.

## <a name="syntax"></a>Sözdizimi

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

Yok.

### <a name="child-elements"></a>Alt öğeleri

Öğe  |Açıklama |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | Belirtilen değere sahip bir yapılandırma ayarı anahtarı ekler |

### <a name="parent-elements"></a>Üst öğeler

Öğe  |Açıklama |
---------|---------|
[\<configuration>](../configuration-element.md) | Ortak dil çalışma zamanı ve Windows Forms uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğe |

## <a name="remarks"></a>Açıklamalar

.NET Framework 4,7 ' den başlayarak, `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework son sürümlerinde eklenen özelliklerden yararlanmak için Windows Forms uygulamalarını yapılandırmanıza olanak tanır.

`<System.Windows.Forms.ApplicationConfigurationSection>`Öğesi [`<add>`](windows-forms-add-configuration-element.md) , her biri belirli bir yapılandırma ayarını tanımlayan bir veya daha fazla alt öğe içerebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma dosyası şeması](../index.md)
- [Windows Forms yüksek DPı desteği](../../../winforms/high-dpi-support-in-windows-forms.md)
