---
title: 'Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 2e2bc70b108991fd4e3c138bfac5bff942173e33
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856118"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama

Bu örnek, <xref:System.Windows.Controls.TextBox.Text%2A> bir <xref:System.Windows.Controls.TextBox> denetimin ilk metin içeriğini ayarlamak için özelliğinin nasıl kullanılacağını gösterir.

> [!NOTE]
> `<TextBox.Text>` <xref:System.Windows.Markup.ContentPropertyAttribute> <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> Örneğin sürümü, her düğmenin <xref:System.Windows.Controls.TextBox> içeriği metin etrafında Etiketler kullanabilse de, özniteliği özelliği özelliğine uyguladığı için bu gerekli değildir. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Daha fazla bilgi için bkz. [xaml genel bakış (WPF)](../advanced/xaml-overview-wpf.md).

## <a name="example"></a>Örnek

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Örnek

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Ayrıca bkz.

- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
