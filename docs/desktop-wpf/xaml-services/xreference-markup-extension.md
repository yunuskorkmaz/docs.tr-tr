---
title: x:Reference Biçimlendirme Uzantısı
ms.date: 03/30/2017
helpviewer_keywords:
- x:Reference markup extension [XAML Services]
- XAML [XAML Services], x:Reference Markup Extension
- Reference markup extension [XAML Services]
ms.assetid: 2982e68b-d26b-4aa3-826a-34c57a9c5199
ms.openlocfilehash: f06e259893111a436e5afe2df754c3edee326d54
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071383"
---
# <a name="xreference-markup-extension"></a>x:Reference Biçimlendirme Uzantısı

XAML biçimlendirmesinde başka bir yerde bildirilen bir örneğe başvurur. Başvuru, bir `x:Name`öğenin.

## <a name="xaml-attribute-usage"></a>XAML Öznitelik Kullanımı

```xaml
<object property="{x:Reference instancexName}" .../>
```

## <a name="xaml-object-element-usage"></a>XAML Nesne Öğesi Kullanımı

```xaml
<object>
  <object.property>
    <x:Reference Name="instancexName"/>
  </object.property>
</object>
```

## <a name="xaml-values"></a>XAML Değerleri

|||
|-|-|
|`instancexName`|Başvurulan örneğin `x:Name` değeri <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>(veya tanımlanan özelliğin değeri).|

## <a name="remarks"></a>Açıklamalar

`x:Reference`WPF gibi belirli çerçevelerde başka türlü uygulanan bir öğe başvuru kavramı için XAML dil düzeyinde destek sağlar.

## <a name="xreference-and-wpf"></a>x:Referans ve WPF

WPF ve XAML 2006'da, eleman başvuruları <xref:System.Windows.Data.Binding.ElementName%2A> bağlayıcıçerçeve düzeyindeki özelliğiyle ele alınır. Çoğu WPF uygulaması ve senaryosu <xref:System.Windows.Data.Binding.ElementName%2A> için bağlama yine de kullanılmalıdır. Bu genel kılavuzun istisnaları, veri bağlamı veya veri bağlamayı pratik hale getiren diğer kapsamlandırma konularının bulunduğu ve biçimlendirme derlemenin söz konusu olmadığı durumları içerebilir.

`x:Reference`XAML 2009'da tanımlanan bir yapıdır. WPF'de XAML 2009 özelliklerini kullanabilirsiniz, ancak yalnızca WPF biçimlendirmesi derlenmiş olmayan XAML için kullanabilirsiniz. Biçimlendirmeyle derlenmiş XAML ve XAML'nin BAML formu şu anda XAML 2009 dil anahtar kelimelerini ve özelliklerini desteklemez.
