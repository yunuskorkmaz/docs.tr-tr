---
title: "Nasıl yapılır: TextBox'tan Satır Koleksiyonu Alma"
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: b7b2f1c2e071388635fb50b1e3573fd7f44334dd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224643"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Nasıl yapılır: TextBox'tan Satır Koleksiyonu Alma
Bu örnekte, metni satır koleksiyonu alma işlemi gösterilmektedir bir <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alan basit bir yöntemi gösterir. bir <xref:System.Windows.Controls.TextBox> döndürür ve bağımsız değişkeni olarak bir <xref:System.Collections.Specialized.StringCollection> metin satırlarını içeren **TextBox**.  <xref:System.Windows.Controls.TextBox.LineCount%2A> Kaç satır şu anda kullanımda olduğunu belirlemek için kullanılan özellik **TextBox**ve <xref:System.Windows.Controls.TextBox.GetLineText%2A> yöntemi ardından her satırı ayıklamak ve koleksiyona satır eklemek için kullanılır.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextBox Genel Bakışı](textbox-overview.md)
- [RichTextBox Genel Bakışı](richtextbox-overview.md)
