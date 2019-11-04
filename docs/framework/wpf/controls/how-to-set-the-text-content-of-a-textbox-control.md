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
ms.openlocfilehash: 9b16f2d99295a28725255361b0be3ef7f4245fd2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459308"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama

Bu örnek, bir <xref:System.Windows.Controls.TextBox> denetiminin ilk metin içeriğini ayarlamak için <xref:System.Windows.Controls.TextBox.Text%2A> özelliğinin nasıl kullanılacağını gösterir.

> [!NOTE]
> Örneğin [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] sürümü, her düğmenin <xref:System.Windows.Controls.TextBox> içeriği metin etrafında `<TextBox.Text>` etiketlerini kullanabilse de, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Markup.ContentPropertyAttribute> özniteliğini <xref:System.Windows.Controls.TextBox.Text%2A> özelliğine uyguladığı için bu gerekli değildir. Daha fazla bilgi için bkz. [xaml genel bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

## <a name="example"></a>Örnek

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Örnek

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Ayrıca bkz.

- [TextBox Genel Bakış](textbox-overview.md)
- [RichTextBox Genel Bakış](richtextbox-overview.md)
