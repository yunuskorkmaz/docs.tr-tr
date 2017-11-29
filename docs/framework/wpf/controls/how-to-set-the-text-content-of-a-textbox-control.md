---
title: "Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8da173fb91745f83aac2b4461a917c1fff6e9cb4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="9e8ee-102">Nasıl yapılır: TextBox Denetiminin Metin İçeriğini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="9e8ee-102">How to: Set the Text Content of a TextBox Control</span></span>
<span data-ttu-id="9e8ee-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TextBox.Text%2A> ilk metin içeriğini ayarlamak için özellik bir <xref:System.Windows.Controls.TextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="9e8ee-103">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
 <span data-ttu-id="9e8ee-104">**Not** rağmen [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örneğinin sürümü kullanabilir `<TextBox.Text>` etiketleri her düğmenin etrafında <xref:System.Windows.Controls.TextBox> içerik, bu gerekli değildir çünkü <xref:System.Windows.Controls.TextBox> geçerlidir <xref:System.Windows.Markup.ContentPropertyAttribute> özniteliğini <xref:System.Windows.Controls.TextBox.Text%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9e8ee-104">**Note** Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="9e8ee-105">Daha fazla bilgi için bkz: [XAML genel bakış (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="9e8ee-105">For more information, see [XAML Overview (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e8ee-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e8ee-106">Example</span></span>  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a><span data-ttu-id="9e8ee-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e8ee-107">Example</span></span>  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a><span data-ttu-id="9e8ee-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9e8ee-108">See Also</span></span>  
 [<span data-ttu-id="9e8ee-109">TextBox genel bakış</span><span class="sxs-lookup"><span data-stu-id="9e8ee-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="9e8ee-110">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9e8ee-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
