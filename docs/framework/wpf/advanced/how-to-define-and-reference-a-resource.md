---
title: 'Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: e33c86b03d8b18113f3a15b3ab251753958ff5b2
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646506"
---
# <a name="how-to-define-and-reference-a-resource"></a>Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma

Bu örnekte, bir kaynağın nasıl tanımlanılıp başvurulup [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]başvurulup.

## <a name="example"></a>Örnek

Aşağıdaki örnek, iki kaynak türünü <xref:System.Windows.Media.SolidColorBrush> tanımlar: kaynak <xref:System.Windows.Style> ve birkaç kaynak. <xref:System.Windows.Media.SolidColorBrush> Kaynak, `MyBrush` her biri bir <xref:System.Windows.Media.Brush> tür değeri almak birkaç özelliklerin değerini sağlamak için kullanılır. Kaynakları <xref:System.Windows.Style> `PageBackground` `TitleText` ve `Label` her hedef belirli bir denetim türü. Bu stil kaynağı kaynak anahtarıyla başvurulduğunda ve 'de <xref:System.Windows.FrameworkElement.Style%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]tanımlanan birkaç özel denetim öğesinin özelliğini ayarlamak için kullanıldığında, stiller hedeflenen denetimlerde çeşitli özellikler ayarlar.

`Label` Stilin ayarlayıcıları içindeki özelliklerden birinin daha `MyBrush` önce tanımlanan kaynağa da atıfta bulunultak olduğunu unutmayın. Bu yaygın bir tekniktir, ancak kaynakların ayrıştırılmış ve verilen sırayla bir kaynak sözlüğüne girilir hatırlamak önemlidir. [Statik Kaynak İşaretle uzantısını](staticresource-markup-extension.md) başka bir kaynaktan başvurmak için kullanırsanız, kaynak sözlüğünde bulunan sıra yla da istenir. Başvuruda bulunduğunuz herhangi bir kaynağın kaynak koleksiyonunda, kaynak tanığının istendiği yerden daha öncetan tanımlanmasından emin olun. Gerekirse, kaynak yerine çalışma zamanında kaynağa başvurmak için dinamik kaynak [biçimlendirme uzantısı](dynamicresource-markup-extension.md) kullanarak kaynak başvurularının katı oluşturma sırası etrafında çalışabilirsiniz, ancak bu Dinamik Kaynak tekniğinin performans sonuçları olduğunu unutmayın. Ayrıntılar için [XAML Kaynakları'na](../../../desktop-wpf/fundamentals/xaml-resources-define.md)bakın.

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](../../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
