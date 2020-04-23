---
title: x:Null Biçimlendirme Uzantısı
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: b83e893f951c15eca69fbb6b002369dd723ca469
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071432"
---
# <a name="xnull-markup-extension"></a>x:Null Biçimlendirme Uzantısı

Bir XAML üyesi için bir değer olarak belirtir. `null`

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>Açıklamalar

C# ve C++'da null başvurusu için kullanılan anahtar kelime null'dur. Null reference için Microsoft Visual Basic `Nothing`anahtar sözcüğü, xaml ile ilişkilendirdiğiniz kod arkası dili ne olursa olsun her zaman XAML kullanımı olarak kullanılır. `{x:Null}`

`x:Null` Biçimlendirme uzantısı ayarlanan özellikleri vardır.

Null kullanımı genellikle bir CLR <xref:System.Nullable%601> değerinin XAML üye maruziyeti ile ilişkilidir.

`x:Null` Tüm XAML biçimlendirme uzantıları gibi biçimlendirme uzantısı, öznitelik değerlerinin işlenmesinden gerçek veya olay işleyicisi başvurularından başka bir şekilde kaçmak için ayraçları ()`{,}`kullanır. Öznitelik sözdizimi, bu biçimlendirme uzantısı ile en sık kullanılan sözdizimidir. Bir nesne öğesi `<x:Null />` sözdizimi teknik olarak mümkündür, ancak `x:Null` biçimlendirme uzantısı konumsal parametreler veya yapı bağımsız değişkenleri olmadığından nadiren kullanılır.

Biçimlendirme uzantıları hakkında daha fazla bilgi için [bkz.](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)

.NET XAML Hizmetleri'nde, bu biçimlendirme uzantısı <xref:System.Windows.Markup.NullExtension> için işleme sınıf tarafından tanımlanır.

## <a name="wpf-usage-notes"></a>WPF Kullanım Notları

Başvuru `null` türü bağımlılık özelliği için ilk ayarlanmamış değerin mutlaka olmadığını unutmayın. İlk varsayılan değer her bağımlılık özelliği için değişebilir ve özelliğe özgü meta verilere dayalı olabilir. Birçok bağımlılık özelliği, `null` doğrulama geri arama uygulamaları nedeniyle biçimlendirme veya kod yoluyla bir değer olarak kabul etmez. Bağımlılık özellikleri hakkında daha fazla bilgi için [bkz.](../../framework/wpf/advanced/dependency-properties-overview.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
