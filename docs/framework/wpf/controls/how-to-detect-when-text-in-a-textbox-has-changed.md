---
title: 'Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1befd18220488334319a55bce2ce602aef20d3d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552958"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Nasıl yapılır: TextBox İçindeki Metin Değiştirildiğinde Algılama
Bu örnek kullanmanın tek yolu gösterir <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> bir yöntem yürütülmeye olay her metinde bir <xref:System.Windows.Controls.TextBox> denetim değişti.  
  
 Arka plan kodu sınıfında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içeren <xref:System.Windows.Controls.TextBox> değişiklikler için izlemek istediğiniz denetimi Ekle olduğunda çağrılacak bir yöntem <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay etkinleşir.  Bu yöntem tarafından beklenenle eşleşen bir imzaya sahip olmalıdır <xref:System.Windows.Controls.TextChangedEventHandler> temsilci.  
  
 Olay işleyicisi çağrılır her içeriğini <xref:System.Windows.Controls.TextBox> denetim değiştirilirse, bir kullanıcı veya program aracılığıyla.  
  
 **Not:** bu olay tetiklenen <xref:System.Windows.Controls.TextBox> denetim oluşturulur ve başlangıçta metin ile doldurulur.  
  
## <a name="example"></a>Örnek  
 İçinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlayan, <xref:System.Windows.Controls.TextBox> denetlemek, belirtin <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> özniteliği olay işleyicisi yöntem adıyla eşleşen bir değere sahip.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Örnek  
 Arka plan kodu sınıfında [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] içeren <xref:System.Windows.Controls.TextBox> değişiklikler için izlemek istediğiniz denetimi Ekle olduğunda çağrılacak bir yöntem <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> olay etkinleşir.  Bu yöntem tarafından beklenenle eşleşen bir imzaya sahip olmalıdır <xref:System.Windows.Controls.TextChangedEventHandler> temsilci.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 Olay işleyicisi çağrılır her içeriğini <xref:System.Windows.Controls.TextBox> denetim değiştirilirse, bir kullanıcı veya program aracılığıyla.  
  
 **Not:** bu olay tetiklenen <xref:System.Windows.Controls.TextBox> denetim oluşturulur ve başlangıçta metin ile doldurulur.  
  
 Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
