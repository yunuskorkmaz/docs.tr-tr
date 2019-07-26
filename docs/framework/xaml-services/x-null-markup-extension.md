---
title: x:Null İşaretleme Uzantısı
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
ms.openlocfilehash: 7dbea2c7d4010d8defc572dbdc14a0dfd6d7601e
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484715"
---
# <a name="xnull-markup-extension"></a>x:Null İşaretleme Uzantısı
XAML `null` üyesi için değer olarak belirtir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Ve C# C++ içindeki null başvurusunun anahtar sözcüğü null. Bir null başvurusunun Microsoft Visual Basic anahtar sözcüğü vardır `Nothing`, ancak xaml ile ilişkilendirdiğiniz kod arkasındaki dilin ne olursa olsun, her zaman XAML kullanımı olarak kullanırsınız. `{x:Null}`  
  
 `x:Null` Biçimlendirme uzantısının ayarlanabilir bir özelliği yok.  
  
 Null kullanımı genellikle bir clr <xref:System.Nullable%601> değerinin xaml üye pozlaması ile ilişkilendirilir.  
  
 Biçimlendirme uzantısı, tüm XAML biçimlendirme uzantıları gibi, öznitelik değerlerinin işlenmesini, değişmez`{,}`değer veya olay işleyici başvuruları dışında bırakmak için parantez () kullanır. `x:Null` Öznitelik sözdizimi, bu biçimlendirme uzantısıyla en sık kullanılan sözdizimidir. Bir nesne öğesi sözdizimi `<x:Null />` teknik açıdan olasıdır, ancak `x:Null` biçimlendirme uzantısının Konumsal parametre veya oluşturma bağımsız değişkenleri olmadığından nadiren kullanılır.  
  
 Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 .NET Framework XAML hizmetlerinde, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.Markup.NullExtension> sınıfı tarafından tanımlanır.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 `null` Bir başvuru türü bağımlılık özelliği için ilk önceden ayarlama değeri olması gerekmediğini unutmayın. İlk varsayılan değer her bağımlılık özelliği için farklılık gösterebilir ve özelliğe özgü meta verileri temel alabilir. Birçok bağımlılık özelliği, doğrulama geri `null` çağırma uygulamalarından dolayı biçimlendirme veya kod aracılığıyla bir değer olarak kabul etmez. Bağımlılık özellikleri hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML'ye Genel Bakış (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [İşaretleme Uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
