---
title: 'Nasıl yapılır: Denetime FocusVisualStyle Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: ae7820dac011425251d087dd4109c3f40bdd308c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493254"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Nasıl yapılır: Denetime FocusVisualStyle Uygulama
Bu örnek nasıl odak görsel stili kaynakları oluşturup bir denetime stil uygulama gösterir kullanarak <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, denetimin klavye odaklı içinde olduğunda yalnızca geçerli olan ek denetim birleştirmesini oluşturur bir stil tanımlar [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Bu stil ile tanımlayarak gerçekleştirilir bir <xref:System.Windows.Controls.ControlTemplate>, o stilin ayarlanırken bir kaynak olarak başvuran sonra <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği.  
  
 Benzeyen bir kenarlık dış bir dikdörtgen dışında dikdörtgen alan yerleştirilir. Aksi takdirde değiştirilmediği sürece stili boyutlandırması kullanır <xref:System.Windows.FrameworkElement.ActualHeight%2A> ve <xref:System.Windows.FrameworkElement.ActualWidth%2A> dikdörtgen denetimi odak görsel stili burada uygulanır. Bu örnek için negatif değerler ayarlar <xref:System.Windows.FrameworkElement.Margin%2A> kenarlık biraz odaklı denetimin dışında görünür hale getirmek için.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> olan gelen herhangi bir denetim şablonu stilini eklenebilir ya da açık bir stil veya bir tema stili; bir denetim için birincil stil yine de kullanarak oluşturulabilir bir <xref:System.Windows.Controls.ControlTemplate> ve o stilin ayarını <xref:System.Windows.FrameworkElement.Style%2A> özelliği.  
  
 Odak görsel stilleri kullanılmalıdır tutarlı bir şekilde bir tema veya bir kullanıcı Arabirimi odaklanabilir her öğe için farklı bir kullanmak yerine. Ayrıntılar için bkz [denetimleri ve FocusVisualStyle odak için stil oluşturma](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Stil ve Şablon Oluşturma](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)
