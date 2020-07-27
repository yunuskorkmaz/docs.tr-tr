---
title: 'Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama'
description: Metin özelliğini kullanarak bir Windows Presentation Foundation metin kutusu denetiminin ilk metin içeriğini ayarlama hakkında bilgi edinin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 41efb69e297b3c6fdb1203c358dcc72d7a9f806f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168046"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama

Bu örnek, <xref:System.Windows.Controls.TextBox.Text%2A> bir denetimin ilk metin içeriğini ayarlamak için özelliğinin nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TextBox> .

> [!NOTE]
> [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Örneğin sürümü, `<TextBox.Text>` her düğmenin içeriği metin etrafında Etiketler kullanabilse de, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Markup.ContentPropertyAttribute> özniteliği özelliği özelliğine uyguladığı için bu gerekli değildir <xref:System.Windows.Controls.TextBox.Text%2A> . Daha fazla bilgi için bkz. [xaml genel bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

## <a name="example"></a>Örnek

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Örnek

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Ayrıca bkz.

- [TextBox Genel Bakışı](textbox-overview.md)
- [RichTextBox Genel Bakışı](richtextbox-overview.md)
