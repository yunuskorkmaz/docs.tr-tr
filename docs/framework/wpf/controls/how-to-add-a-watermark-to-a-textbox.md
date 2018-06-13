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
ms.openlocfilehash: 962d6958de0811863393f930d8672769a50e8265
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550075"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Nasıl yapılır: TextBox'a Filigran Ekleme
Aşağıdaki örnek, kullanılabilirliğini yardımcı olmak gösterilmiştir bir <xref:System.Windows.Controls.TextBox> içinde açıklayıcı arka plan görüntüsü görüntüleyerek <xref:System.Windows.Controls.TextBox> metin kullanıcı girdi kadar bu noktada görüntü kaldırılır. Ayrıca, kullanıcının kendi giriş kaldırırsa arka plan resmini yeniden geri yüklendi. Aşağıdaki şekle bakın.  
  
 ![Arka plan resmi kutusuyla](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
>  Arka plan resmi yerine sonra yalnızca düzenleme Bu örnekte kullanılan neden <xref:System.Windows.Controls.TextBox.Text%2A> özelliği <xref:System.Windows.Controls.TextBox>, arka plan görüntüsü ile veri bağlaması etkilemeyeceğini olduğu.  
  
## <a name="example"></a>Örnek  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
