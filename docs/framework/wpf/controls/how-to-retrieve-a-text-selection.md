---
title: 'Nasıl yapılır: Metin Seçimi Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: 6b25c555d5e6cac93b2e1518b25e7880ab77c866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552018"
---
# <a name="how-to-retrieve-a-text-selection"></a>Nasıl yapılır: Metin Seçimi Alma
Bu örnek kullanmanın tek yolu gösterir <xref:System.Windows.Controls.TextBox.SelectedText%2A> özelliği kullanıcının seçtiği metni almak için bir <xref:System.Windows.Controls.TextBox> denetim.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek tanımını gösterir bir <xref:System.Windows.Controls.TextBox> seçmek için bazı metinleri içeren denetim ve <xref:System.Windows.Controls.Button> belirtilen bir denetimle <xref:System.Windows.Controls.Button.OnClick%2A> yöntemi.  
  
 Bu örnekte, ile ilişkili bir düğme <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olay işleyicisi metin seçimini almak için kullanılır. Kullanıcı düğmesini tıklattığında <xref:System.Windows.Controls.Button.OnClick%2A> yöntemi metin kutusuna tüm seçili metinleri bir dizeye kopyalar. Belirli durumlarda olarak metin seçimini (bir düğmeye tıklama) yanı sıra (metin seçimini dizeye kopyalama) bu seçimle gerçekleştirilecek eylemi kolayca değiştirilebilir çok çeşitli senaryoları uyum sağlayacak şekilde alınır.  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örnekte gösterildiği bir <xref:System.Windows.Controls.Button.OnClick%2A> içinde tanımlanmış düğme için olay işleyicisini [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Bu örnek için.  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
