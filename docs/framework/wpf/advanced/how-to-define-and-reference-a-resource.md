---
title: 'Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma'
ms.date: 03/30/2017
helpviewer_keywords:
- resources [WPF], defining
- defining resources [WPF]
- resources [WPF], referencing
- referencing resources [WPF]
ms.assetid: b86b876b-0a10-489b-9a5d-581ea9b32406
ms.openlocfilehash: 347804f0ce6dd3b907d3ac088248a64569a63695
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543500"
---
# <a name="how-to-define-and-reference-a-resource"></a>Nasıl yapılır: Kaynağı Tanımlama ve Kaynağa Başvurma
Bu örnek bir kaynak tanımlamak ve bir öznitelik kullanarak başvuru gösterilmektedir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki tür kaynak tanımlar: bir <xref:System.Windows.Media.SolidColorBrush> kaynağı ve birkaç <xref:System.Windows.Style> kaynakları. <xref:System.Windows.Media.SolidColorBrush> Kaynak `MyBrush` herbiri çeşitli özelliklerin değerini sağlamak için kullanılan bir <xref:System.Windows.Media.Brush> değeri yazın. <xref:System.Windows.Style> Kaynakları `PageBackground`, `TitleText` ve `Label` her hedef belirli denetim türü. Stil kaynağı kaynak anahtarı tarafından başvurulan ve ayarlamak için kullanılan stiller farklı özellikler çeşitli hedeflenen denetimler üzerinde ayarlanır <xref:System.Windows.FrameworkElement.Style%2A> tanımlanan birkaç özel denetim öğelerinin özellik [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Not Bu özelliklerden birini ayarlayıcıları içindeki `Label` stili de başvuran `MyBrush` önceden tanımlanmış kaynak. Bu ortak bir tekniktir, ancak kaynakları ayrıştırılır ve bir kaynak sözlüğü verildikleri sırada girilen unutmamak önemlidir. Kaynaklar ayrıca kullanırsanız sözlükte bulundukları sıraya göre istenen [StaticResource biçimlendirme uzantısı](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md) onlardan içindeki başka bir kaynak başvurmak için. Başvuru herhangi bir kaynağa burada bu kaynak ardından istenen daha kaynaklar koleksiyonu içinde daha önce tanımlandığından emin olun. Gerekirse, kaynak referanslarının kesin oluşturulma sırasını kullanarak çalışabilirsiniz bir [DynamicResource Biçimlendirme Uzantısı](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md) çalışma zamanında bunun yerine, referans için ancak, farkında olmalıdır, bu DynamicResource Teknik performans sonuçları vardır. Ayrıntılar için bkz [XAML kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
 [!code-xaml[FEResource#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEResource/CS/default.xaml#xaml)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XAML Kaynakları](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
