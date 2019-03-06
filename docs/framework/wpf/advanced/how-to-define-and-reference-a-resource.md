---
title: 'Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: c429e3373ef1b78fba12dd5125af653f66cf5d74
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371586"
---
# <a name="how-to-define-and-reference-a-resource"></a>Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma
Bu örnek, bir kaynağı tanımlama ve bir öznitelikte kullanarak başvuru gösterilmektedir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki tür kaynak tanımlar: bir <xref:System.Windows.Media.SolidColorBrush> kaynağı ve birkaç <xref:System.Windows.Style> kaynakları. <xref:System.Windows.Media.SolidColorBrush> Kaynak `MyBrush` herbiri birkaç özellik değeri sağlamak için kullanılan bir <xref:System.Windows.Media.Brush> değeri yazın. <xref:System.Windows.Style> Kaynakları `PageBackground`, `TitleText` ve `Label` her hedef belirli denetim türü. Stil kaynağı kaynak anahtarı tarafından başvurulan ve ayarlamak için kullanılan stilleri çeşitli farklı özellikler hedeflenen denetimlere ayarlayın. <xref:System.Windows.FrameworkElement.Style%2A> özelliği içinde tanımlanan çeşitli özel denetim öğelerinin [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Not Bu özelliklerden biri ayarlayıcılar içinde `Label` stili de başvuran `MyBrush` daha önce tanımlanan kaynak. Bu sık kullanılan bir yöntemdir, ancak kaynaklar ayrıştırılır ve bir kaynak sözlüğü verildikleri sırada girilen unutmamak önemlidir. Kaynakları da kullanırsanız, sözlük içinde bulundukları sıraya göre istenen [StaticResource işaretleme uzantısı](staticresource-markup-extension.md) bunları içinde başka bir kaynak başvurmak için. Burada, kaynak ardından istenen daha kaynakları koleksiyonu içinde başvuru herhangi bir kaynağa daha önce tanımlanmış olduğundan emin olun. Gerekirse, kaynak referanslarının kesin oluşturulma sırasını geçici bir çözüm kullanarak çalışabilirsiniz bir [DynamicResource işaretleme uzantısı](dynamicresource-markup-extension.md) bunun yerine, çalışma zamanında başvurmak için ancak bilmeniz gerekir, bu DynamicResource Teknik performans sonuçları vardır. Ayrıntılar için bkz [XAML kaynakları](xaml-resources.md).  
  
 [!code-xaml[FEResource#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [XAML Kaynakları](xaml-resources.md)
- [Stil ve Şablon Oluşturma](../controls/styling-and-templating.md)
