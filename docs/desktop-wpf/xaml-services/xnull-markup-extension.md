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
ms.openlocfilehash: f4971d61d11ec14eaeac2d2f202353e4921b9325
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90549450"
---
# <a name="xnull-markup-extension"></a>x:Null Biçimlendirme Uzantısı

`null`Xaml üyesi için değer olarak belirtir.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object property="{x:Null}" .../>
```

## <a name="remarks"></a>Açıklamalar

C# ve C++ içindeki null başvurusunun anahtar sözcüğü null. Bir null başvurusunun Microsoft Visual Basic anahtar sözcüğü vardır `Nothing` , ancak `{x:Null}` XAML ile ilişkilendirdiğiniz kod arkasındaki dilin ne olursa olsun, her zaman XAML kullanımı olarak kullanırsınız.

`x:Null`Biçimlendirme uzantısının ayarlanabilir bir özelliği yok.

Null kullanımı genellikle bir CLR değerinin XAML üye pozlaması ile ilişkilendirilir <xref:System.Nullable%601> .

`x:Null`Biçimlendirme uzantısı, tüm XAML biçimlendirme uzantıları gibi, `{,}` öznitelik değerlerinin işlenmesini, değişmez değer veya olay işleyici başvuruları dışında bırakmak için parantez () kullanır. Öznitelik sözdizimi, bu biçimlendirme uzantısıyla en sık kullanılan sözdizimidir. Bir nesne öğesi sözdizimi `<x:Null />` Teknik açıdan olasıdır, ancak `x:Null` biçimlendirme uzantısının Konumsal parametre veya oluşturma bağımsız değişkenleri olmadığından nadiren kullanılır.

Biçimlendirme uzantıları hakkında daha fazla bilgi için bkz. [Biçimlendirme uzantıları ve WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml).

.NET XAML hizmetlerinde, bu biçimlendirme uzantısının işlenmesi sınıfı tarafından tanımlanır <xref:System.Windows.Markup.NullExtension> .

## <a name="wpf-usage-notes"></a>WPF kullanım notları

`null`Bir başvuru türü bağımlılık özelliği için ilk önceden ayarlama değeri olması gerekmediğini unutmayın. İlk varsayılan değer her bağımlılık özelliği için farklılık gösterebilir ve özelliğe özgü meta verileri temel alabilir. Birçok bağımlılık özelliği `null` , doğrulama geri çağırma uygulamalarından dolayı biçimlendirme veya kod aracılığıyla bir değer olarak kabul etmez. Bağımlılık özellikleri hakkında daha fazla bilgi için bkz. [bağımlılık özelliklerine genel bakış](/dotnet/desktop/wpf/advanced/dependency-properties-overview).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML'ye Genel Bakış (WPF)](../fundamentals/xaml.md)
- [Biçimlendirme Uzantıları ve WPF XAML](/dotnet/desktop/wpf/advanced/markup-extensions-and-wpf-xaml)
