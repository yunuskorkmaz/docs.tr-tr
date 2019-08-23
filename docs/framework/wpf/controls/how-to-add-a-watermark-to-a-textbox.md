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
ms.openlocfilehash: abe276c686d394ded13ec03f08deae65e4098d03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923571"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Nasıl yapılır: TextBox'a Filigran Ekleme
Aşağıdaki örnek, Kullanıcı metin girişi <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox> yapılıncaya kadar ' ın içinde açıklayıcı bir arka plan görüntüsü görüntüleyerek bir öğesinin kullanılabilirliğine nasıl yardımcı olduğunu gösterir. Ayrıca, Kullanıcı girişlerini kaldırırsa arka plan görüntüsü yeniden geri yüklenir. Aşağıdaki çizime bakın.  
  
 ![Arka plan resmi olan bir metin kutusu](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
> Bu örnekte, bir arka plan resminin, <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox>özelliğini işlemek yerine kullanıldığı neden, arka plan resminin veri bağlamayı etkilememesini sağlamaktır.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
