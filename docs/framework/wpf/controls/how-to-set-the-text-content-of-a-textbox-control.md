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
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="1f396-103">Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="1f396-103">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="1f396-104">Bu örnek, <xref:System.Windows.Controls.TextBox.Text%2A> bir denetimin ilk metin içeriğini ayarlamak için özelliğinin nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="1f396-104">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="1f396-105">[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Örneğin sürümü, `<TextBox.Text>` her düğmenin içeriği metin etrafında Etiketler kullanabilse de, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Markup.ContentPropertyAttribute> özniteliği özelliği özelliğine uyguladığı için bu gerekli değildir <xref:System.Windows.Controls.TextBox.Text%2A> .</span><span class="sxs-lookup"><span data-stu-id="1f396-105">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="1f396-106">Daha fazla bilgi için bkz. [xaml genel bakış (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="1f396-106">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>

## <a name="example"></a><span data-ttu-id="1f396-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f396-107">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="1f396-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f396-108">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="1f396-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f396-109">See also</span></span>

- [<span data-ttu-id="1f396-110">TextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="1f396-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="1f396-111">RichTextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="1f396-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
