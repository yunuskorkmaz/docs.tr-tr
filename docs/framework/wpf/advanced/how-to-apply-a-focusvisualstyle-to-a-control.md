---
title: 'Nasıl yapılır: Denetime FocusVisualStyle Uygulama'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: b44330ee7554f953389556bd62ff49db120b5db9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459813"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>Nasıl yapılır: Denetime FocusVisualStyle Uygulama
Bu örnek, <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliğini kullanarak kaynaklarda odak görsel stilinin nasıl oluşturulacağını ve stilin bir denetime nasıl uygulanacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yalnızca denetimin [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]odaklandığı zaman geçerli olan ek denetim birleştirmesini oluşturan bir stil tanımlar. Bu, <xref:System.Windows.Controls.ControlTemplate>bir stil tanımlayarak ve <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> özelliği ayarlanırken bu stile kaynak olarak başvurularak yapılır.  
  
 Bir kenarlığa benzeyen dış Dikdörtgen dikdörtgen alanın dışına yerleştirilir. Aksi belirtilmedikçe, stilin boyutlandırılması, odak görsel stilinin uygulandığı dikdörtgen denetimin <xref:System.Windows.FrameworkElement.ActualHeight%2A> ve <xref:System.Windows.FrameworkElement.ActualWidth%2A> kullanır. Bu örnek, kenarlığın odaklanmış denetimin dışında biraz görünmesi için <xref:System.Windows.FrameworkElement.Margin%2A> negatif değerlerini ayarlar.  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>, açık bir stille veya tema stilinden gelen herhangi bir denetim şablonu stiline eklenebilir; bir denetimin birincil stili hala bir <xref:System.Windows.Controls.ControlTemplate> kullanılarak oluşturulabilir ve bu stil <xref:System.Windows.FrameworkElement.Style%2A> özelliğine ayarlanabilir.  
  
 Odak görsel stilleri, odaklanacak her öğe için farklı bir tane kullanmak yerine bir tema veya Kullanıcı arabirimi genelinde sürekli olarak kullanılmalıdır. Ayrıntılar için bkz. [denetimlerde odak Için stil oluşturma ve FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [Stil ve Şablon Oluşturma](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Denetimlerde Odak için Stil Oluşturma ve FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
