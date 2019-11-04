---
title: 'Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 89471c45aabd9f3415c45a2e8af41d1a52900324
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460181"
---
# <a name="how-to-define-and-reference-a-resource"></a>Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma

Bu örnek, bir kaynağın nasıl tanımlanacağını ve [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]bir özniteliği kullanılarak nasıl başvurulacağını gösterir.

## <a name="example"></a>Örnek

Aşağıdaki örnek iki tür kaynak tanımlar: bir <xref:System.Windows.Media.SolidColorBrush> kaynağı ve birkaç <xref:System.Windows.Style> kaynağı. <xref:System.Windows.Media.SolidColorBrush> kaynak `MyBrush`, her birinin <xref:System.Windows.Media.Brush> bir tür değeri alan birkaç özellik değeri sağlamak için kullanılır. <xref:System.Windows.Style> kaynakları `PageBackground`, `TitleText` ve `Label` her hedefle belirli bir denetim türünü hedefler. Stiller, kaynak anahtarı tarafından bu stil kaynağına başvurulduğunda hedeflenen denetimlerde çeşitli özellikler ayarlar ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]tanımlanan çeşitli belirli denetim öğelerinin <xref:System.Windows.FrameworkElement.Style%2A> özelliğini ayarlamak için kullanılır.

`Label` stilin ayarlayıcılarındaki özelliklerden birinin, daha önce tanımlanan `MyBrush` kaynağına de başvurdığına unutmayın. Bu, yaygın bir tekniktir, ancak kaynakların ayrıştırılıp verildikleri sırayla bir kaynak sözlüğüne girildiğini unutmamak önemlidir. Aynı zamanda, başka bir kaynağın içinden başvuruda bulunmak için [StaticResource Işaretleme uzantısını](staticresource-markup-extension.md) kullanırsanız, bu, sözlükte bulunan sırada da istenir. Referans yaptığınız herhangi bir kaynağın, kaynak koleksiyonunun daha önce kaynağın istendiği yerin içinde tanımlandığından emin olun. Gerekirse, bunun yerine çalışma zamanında kaynağa başvurmak için bir [DynamicResource Işaretleme uzantısı](dynamicresource-markup-extension.md) kullanarak kaynak başvurularının katı oluşturma sırasını geçici olarak çözebilirsiniz, ancak bu DynamicResource tekniğinin performansa sahip olduğunu bilmeniz gerekir larının. Ayrıntılar için bkz. [xaml kaynakları](xaml-resources.md).

[!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]

## <a name="see-also"></a>Ayrıca bkz.

- [XAML Kaynakları](xaml-resources.md)
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
