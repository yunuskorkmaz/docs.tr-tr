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
ms.openlocfilehash: ff82b0bfc1983240431e582dbd78778dc4469241
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459936"
---
# <a name="xnull-markup-extension"></a>x:Null Biçimlendirme Uzantısı
XAML üyesi için değer olarak `null` belirtir.  
  
## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Ve C# C++ içindeki null başvurusunun anahtar sözcüğü null. Bir null başvurusunun Microsoft Visual Basic anahtar sözcüğü `Nothing`, ancak XAML ile ilişkilendirdiğiniz arka plan kod diline bakılmaksızın `{x:Null}` her zaman XAML kullanımı olarak kullanırsınız.  
  
 `x:Null` biçimlendirme uzantısının ayarlanabilir bir özelliği yok.  
  
 Null kullanımı genellikle CLR <xref:System.Nullable%601> değerinin XAML üye pozlaması ile ilişkilendirilir.  
  
 Tüm XAML biçimlendirme uzantıları gibi `x:Null` biçimlendirme uzantısı, öznitelik değerlerinin işlenmesini, değişmez değer veya olay işleyici başvuruları dışında bırakmak için parantez (`{,}`) kullanır. Öznitelik sözdizimi, bu biçimlendirme uzantısıyla en sık kullanılan sözdizimidir. Bir nesne öğesi sözdizimi `<x:Null />` teknik açıdan olasıdır, ancak `x:Null` işaretleme uzantısının Konumsal parametre veya oluşturma bağımsız değişkenleri olmadığından nadiren kullanılır.  
  
 Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md).  
  
 .NET Framework XAML hizmetlerinde, bu biçimlendirme uzantısının işlenmesi <xref:System.Windows.Markup.NullExtension> sınıfı tarafından tanımlanır.  
  
## <a name="wpf-usage-notes"></a>WPF kullanım notları  
 `null`, başvuru türü bağımlılık özelliği için ilk önceden ayarlama değeri gerekmediğini unutmayın. İlk varsayılan değer her bağımlılık özelliği için farklılık gösterebilir ve özelliğe özgü meta verileri temel alabilir. Birçok bağımlılık özelliği, doğrulama geri çağırma uygulamalarından dolayı biçimlendirme veya kod aracılığıyla `null` değer olarak kabul etmez. Bağımlılık özellikleri hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](../wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML'ye Genel Bakış (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [İşaretleme Uzantıları ve WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
