---
title: "Nasıl yapılır: TextBox'a Filigran Ekleme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: 1ab8c0f9274f4d461c9c2be04ec0aaca5e753c7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531138"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Nasıl yapılır: TextBox'a Filigran Ekleme
Aşağıdaki örnek ın kullanılabilirliğine yardımcı olma gösterilmiştir bir <xref:System.Windows.Controls.TextBox> açıklayıcı arka plan görüntüsü içinde görüntüleyerek <xref:System.Windows.Controls.TextBox> metin kullanıcı girişlerinin kadar bu noktada görüntü kaldırılır. Ayrıca, kullanıcının kendi giriş kaldırırsa arka plan resmini yeniden geri yüklenir. Aşağıdaki resme bakın.  
  
 ![TextBox ile arka plan görüntüsü](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
>  Arka plan görüntüsü yerine sonra yalnızca düzenleme Bu örnekte kullanılan nedeni <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.TextBox>, olan bir arka plan görüntüsü ile veri bağlaması müdahale etmez.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
