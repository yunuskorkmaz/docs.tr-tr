---
title: "Nasıl yapılır: TextBox'dan Satır Koleksiyonu Alma"
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: a63470c6f0db72340f482bf638910685aa3f461f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561770"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Nasıl yapılır: TextBox'dan Satır Koleksiyonu Alma
Bu örnekte, metni satır koleksiyonu alma işlemi gösterilmektedir bir <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alan basit bir yöntemi gösterir. bir <xref:System.Windows.Controls.TextBox> döndürür ve bağımsız değişkeni olarak bir <xref:System.Collections.Specialized.StringCollection> metin satırlarını içeren **TextBox**.  <xref:System.Windows.Controls.TextBox.LineCount%2A> Kaç satır şu anda kullanımda olduğunu belirlemek için kullanılan özellik **TextBox**ve <xref:System.Windows.Controls.TextBox.GetLineText%2A> yöntemi ardından her satırı ayıklamak ve koleksiyona satır eklemek için kullanılır.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
