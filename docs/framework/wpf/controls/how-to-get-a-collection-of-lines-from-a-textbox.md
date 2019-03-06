---
title: "Nasıl yapılır: TextBox'dan Satır Koleksiyonu Alma"
ms.date: 03/30/2017
helpviewer_keywords:
- lines [WPF], getting collection of
- TextBox control [WPF], getting collection of lines
ms.assetid: a12f529d-b926-47f6-92bf-cad5f17b532a
ms.openlocfilehash: 1aa73e55a3fdfd658c6a337b598dff96244ace40
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354199"
---
# <a name="how-to-get-a-collection-of-lines-from-a-textbox"></a>Nasıl yapılır: TextBox'dan Satır Koleksiyonu Alma
Bu örnekte, metni satır koleksiyonu alma işlemi gösterilmektedir bir <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, alan basit bir yöntemi gösterir. bir <xref:System.Windows.Controls.TextBox> döndürür ve bağımsız değişkeni olarak bir <xref:System.Collections.Specialized.StringCollection> metin satırlarını içeren **TextBox**.  <xref:System.Windows.Controls.TextBox.LineCount%2A> Kaç satır şu anda kullanımda olduğunu belirlemek için kullanılan özellik **TextBox**ve <xref:System.Windows.Controls.TextBox.GetLineText%2A> yöntemi ardından her satırı ayıklamak ve koleksiyona satır eklemek için kullanılır.  
  
 [!code-csharp[TextBox_MiscCode#_TextBox_GetLines](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textbox_getlines)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
