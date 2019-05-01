---
title: Windows Forms Yapılandırma Bölümü
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbb2c4157ba702182056c98c959a60569e8c3d1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786418"
---
# <a name="windows-forms-configuration-section"></a>Windows Forms Yapılandırma Bölümü
Windows Forms yapılandırma ayarlarını depolamak bir Windows Forms uygulaması izin ve özelleştirilmiş uygulama ayarları gibi çoklu monitör desteği, yüksek DPI desteği ve diğer ilgili bilgileri Al önceden tanımlanmış yapılandırma ayarları.

Windows Forms uygulama yapılandırma ayarlarını bir uygulama yapılandırma dosyasına ait depolanan `System.Windows.Forms.ApplicationConfigurationSection` öğesi.

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
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | Belirtilen bir değere sahip bir yapılandırma ayarı anahtarı ekler |

### <a name="parent-elements"></a>Üst öğeler

Öğe  |Açıklama |
---------|---------|
[\<Yapılandırma >](../configuration-element.md) | Kök öğe her yapılandırma dosyasında ortak dil çalışma zamanı ile Windows Forms uygulamaları tarafından kullanılan |

## <a name="remarks"></a>Açıklamalar

.NET Framework 4.7 ile başlayan `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi .NET Framework'ün en son sürümlerde eklenen özelliklerden yararlanmak için Windows Forms uygulamaları yapılandırmanıza imkan sağlar. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Bir veya daha fazla alt öğe içerebilir [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) öğeleri, her biri belirli yapılandırma ayarını tanımlar.

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../index.md)
- [Windows Forms'ta yüksek DPI desteği](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
