---
title: Windows Forms Yapılandırma Bölümü
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e76e11ef8bb39d72cb16655c948354bc326e75bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913093"
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
[\<Yapılandırma >](../configuration-element.md) | Ortak dil çalışma zamanı ve Windows Forms uygulamaları tarafından kullanılan her yapılandırma dosyasındaki kök öğe |

## <a name="remarks"></a>Açıklamalar

.NET Framework 4,7 ' den başlayarak, `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework son sürümlerinde eklenen özelliklerden yararlanmak için Windows Forms uygulamalarını yapılandırmanıza olanak tanır. 

Öğesi, her biri belirli bir yapılandırma ayarını [`<add>`](windows-forms-add-configuration-element.md) tanımlayan bir veya daha fazla alt öğe içerebilir. `<System.Windows.Forms.ApplicationConfigurationSection>`

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../index.md)
- [Windows Forms yüksek DPı desteği](../../../winforms/high-dpi-support-in-windows-forms.md)
