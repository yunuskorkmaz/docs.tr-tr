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
ms.openlocfilehash: 6c0e6e53518d382a2052efa43993d418e35fa0f2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364131"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="ae1c0-102">Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="ae1c0-102">How to: Set the Text Content of a TextBox Control</span></span>
<span data-ttu-id="ae1c0-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TextBox.Text%2A> ilk metin içeriğini ayarlama özelliği bir <xref:System.Windows.Controls.TextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 <span data-ttu-id="ae1c0-104">**Not** rağmen [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örneğinin sürümü kullanması `<TextBox.Text>` etiketleri her düğmenin etrafında <xref:System.Windows.Controls.TextBox> içerik, gerekli değildir çünkü <xref:System.Windows.Controls.TextBox> geçerlidir <xref:System.Windows.Markup.ContentPropertyAttribute> özniteliğini <xref:System.Windows.Controls.TextBox.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-104">**Note** Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="ae1c0-105">Daha fazla bilgi için [XAML genel bakış (WPF)](../advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="ae1c0-105">For more information, see [XAML Overview (WPF)](../advanced/xaml-overview-wpf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae1c0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae1c0-106">Example</span></span>  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a><span data-ttu-id="ae1c0-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae1c0-107">Example</span></span>  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a><span data-ttu-id="ae1c0-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae1c0-108">See also</span></span>
- [<span data-ttu-id="ae1c0-109">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ae1c0-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="ae1c0-110">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ae1c0-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
