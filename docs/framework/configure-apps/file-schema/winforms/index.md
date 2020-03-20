---
title: Windows Forms Yapılandırma Bölümü
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151838"
---
# <a name="windows-forms-configuration-section"></a>Windows Forms Yapılandırma Bölümü
Windows Forms yapılandırma ayarları, windows forms uygulamasının çoklu monitör desteği, yüksek DPI desteği ve diğer önceden tanımlanmış yapılandırma ayarları gibi özelleştirilmiş uygulama ayarları hakkında bilgi depolamasına ve almasına olanak tanır.

Windows Forms uygulama yapılandırma ayarları bir uygulama yapılandırma `System.Windows.Forms.ApplicationConfigurationSection` dosyasının öğesinde depolanır.

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
[`<add>`](windows-forms-add-configuration-element.md) | Belirli bir değere sahip bir yapılandırma ayar anahtarı ekler |

### <a name="parent-elements"></a>Üst öğeler

Öğe  |Açıklama |
---------|---------|
[\<yapılandırma>](../configuration-element.md) | Ortak dil çalışma zamanı ve Windows Forms uygulamaları tarafından kullanılan her yapılandırma dosyasındaki temel öğe |

## <a name="remarks"></a>Açıklamalar

.NET Framework 4.7 ile `<System.Windows.Forms.ApplicationConfigurationSection>` başlayarak, öğe ,.NET Framework'ün son sürümlerinde eklenen özelliklerden yararlanacak şekilde Windows Forms uygulamalarını yapılandırmanızı sağlar.

Öğe, `<System.Windows.Forms.ApplicationConfigurationSection>` her biri belirli [`<add>`](windows-forms-add-configuration-element.md) bir yapılandırma ayarını tanımlayan bir veya daha fazla alt öğe içerebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Yapılandırma Dosyası Şeması](../index.md)
- [Windows Formlarında Yüksek DPI Desteği](../../../winforms/high-dpi-support-in-windows-forms.md)
