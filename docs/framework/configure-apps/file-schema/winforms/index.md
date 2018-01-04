---
title: "Windows Forms Yapılandırma Bölümü"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
ms.workload: dotnet
ms.openlocfilehash: f2d83f5dcf6fa93ceba4d670470bd768a2ee1f88
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-configuration-section"></a>Windows Forms Yapılandırma Bölümü
Önceden tanımlanmış yapılandırma ayarları birden çok monitör desteği, yüksek DPI desteği ve diğer gibi özelleştirilmiş uygulama ayarları hakkında bilgi almak ve Windows Forms yapılandırma ayarlarını depolamak için bir Windows Forms uygulaması izin verin.

Windows Forms uygulama yapılandırma ayarlarını, bir uygulama yapılandırma dosyasının depolandığı `System.Windows.Forms.ApplicationConfigurationSection` öğesi.

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
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | Belirli bir değerle bir yapılandırma ayarı anahtar ekler |

### <a name="parent-elements"></a>Üst öğeler

Öğe  |Açıklama |
---------|---------|
[\<Yapılandırma >](../configuration-element.md) | Her yapılandırma dosyası kök öğesinde ortak dil çalışma zamanı ile Windows Forms uygulamaları tarafından kullanılan |

## <a name="remarks"></a>Açıklamalar

.NET Framework 4.7 ile başlayan `<System.Windows.Forms.ApplicationConfigurationSection>` öğesi, .NET Framework'ün en son sürümlerde eklenen özelliklerden yararlanmak için Windows Forms uygulamaları yapılandırmanıza olanak sağlar. 

`<System.Windows.Forms.ApplicationConfigurationSection>` Öğesi, bir veya daha fazla alt içerebilir [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) öğeleri, her biri belirli bir yapılandırma ayarını tanımlar.

## <a name="see-also"></a>Ayrıca bkz.

[Yapılandırma dosyası şeması](../index.md)   
[Windows Forms'ta yüksek DPI desteği](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
