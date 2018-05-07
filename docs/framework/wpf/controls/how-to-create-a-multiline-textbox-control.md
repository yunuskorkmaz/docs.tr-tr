---
title: 'Nasıl yapılır: Çok Satırlı TextBox Denetimi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 9f4c9e637b686c82b4ec8a4a5d6d3a78d46f97c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Nasıl yapılır: Çok Satırlı TextBox Denetimi Oluşturma
Bu örnek nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlamak için bir <xref:System.Windows.Controls.TextBox> birkaç satırlık metin uyum sağlayacak şekilde otomatik olarak genişletecek denetim.  
  
## <a name="example"></a>Örnek  
 Ayarlama <xref:System.Windows.Controls.TextBox.TextWrapping%2A> özniteliğini **sarmalamak** yeni bir sarmalamak girilen metin neden olacak ne zaman satır köşesine <xref:System.Windows.Controls.TextBox> denetim ulaşıldığında, otomatik olarak genişleterek <xref:System.Windows.Controls.TextBox> yeni bir satır için oda eklenecek denetim gerekli.  
  
 Ayarlama <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> özniteliğini **true** RETURN tuşuna basıldığında otomatik olarak bir kez yeniden genişletme eklenecek yeni bir satır neden <xref:System.Windows.Controls.TextBox> gerekiyorsa, yeni bir satır için oda eklenecek.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Özniteliği için bir kaydırma çubuğunun ekler <xref:System.Windows.Controls.TextBox>, böylece içeriğini <xref:System.Windows.Controls.TextBox> değilse kaydırılabileceğini <xref:System.Windows.Controls.TextBox> çerçeve ya da onu pencere boyutunu genişletir.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.TextWrapping>  
 [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
