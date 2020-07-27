---
title: 'Nasıl yapılır: Çok Satırlı TextBox Denetimi Oluşturma'
description: Windows Presentation Foundation uygulamasında birden çok satırı metin sığacak şekilde genişleyen bir TextBox denetimi tanımlamak için XAML 'yi nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 0a88d4d768884df135afddb491431650b9ba2d24
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166251"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="499cc-103">Nasıl yapılır: Çok Satırlı TextBox Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="499cc-103">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="499cc-104">Bu örnek, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> birden çok metin satırını kapsayacak şekilde otomatik olarak genişletilecek bir denetim tanımlamak için öğesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="499cc-104">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="499cc-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="499cc-105">Example</span></span>  
 <span data-ttu-id="499cc-106"><xref:System.Windows.Controls.TextBox.TextWrapping%2A>Özniteliği **kaydırılacak** şekilde ayarlamak, denetimin kenarına ulaşıldığında girilen metnin yeni bir satıra kaydırılmasına neden olur <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.TextBox> gerekirse yeni bir satıra yer açmak için denetimi otomatik olarak genişleterek.</span><span class="sxs-lookup"><span data-stu-id="499cc-106">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="499cc-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A>Özniteliği **true** olarak ayarlamak, dönüş tuşuna basıldığında yeni bir satırın eklenmesini yeniden otomatik olarak genişleterek, yeni bir satıra yer açmak için bir kez otomatik olarak genişleyen yeni bir satır eklenmesine neden olur <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="499cc-107">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="499cc-108"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>Özniteliği öğesine bir kaydırma çubuğu ekler <xref:System.Windows.Controls.TextBox> . böylece, öğesinin içeriğinin, <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox> kendisini kapsayan çerçeve veya pencere boyutundan daha fazla genişliyorsa kaydırılabilmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="499cc-108">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="499cc-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="499cc-109">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="499cc-110">TextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="499cc-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="499cc-111">RichTextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="499cc-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
