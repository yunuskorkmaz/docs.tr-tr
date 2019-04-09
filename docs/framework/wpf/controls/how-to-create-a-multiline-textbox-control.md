---
title: 'Nasıl yapılır: Çok Satırlı TextBox Denetimi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 29fb4c9498fe163c36e71680242d3ef8cf98c089
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181174"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="f9f9b-102">Nasıl yapılır: Çok Satırlı TextBox Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f9f9b-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="f9f9b-103">Bu örnek nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlamak için bir <xref:System.Windows.Controls.TextBox> birden çok metin satırı uyum sağlayacak şekilde otomatik olarak genişletilecektir denetimi.</span><span class="sxs-lookup"><span data-stu-id="f9f9b-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9f9b-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9f9b-104">Example</span></span>  
 <span data-ttu-id="f9f9b-105">Ayarlama <xref:System.Windows.Controls.TextBox.TextWrapping%2A> özniteliğini **kaydırma** yeni bir kaydırılmasına neden olur ne zaman satır kenarı <xref:System.Windows.Controls.TextBox> denetim ulaşıldığında, otomatik olarak genişleyen <xref:System.Windows.Controls.TextBox> olursa yeni bir satır için yer dahil edilecek denetimi gerekli.</span><span class="sxs-lookup"><span data-stu-id="f9f9b-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="f9f9b-106">Ayarı <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> özniteliğini **true** RETURN tuşuna basıldığında, bir kez daha otomatik olarak eklenmesi için yeni bir satır neden <xref:System.Windows.Controls.TextBox> gerekirse yeni bir satır için yer eklenecek.</span><span class="sxs-lookup"><span data-stu-id="f9f9b-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="f9f9b-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Özniteliği için bir kaydırma çubuğu ekler <xref:System.Windows.Controls.TextBox>, böylece içeriğini <xref:System.Windows.Controls.TextBox> değilse kaydırılabileceğini <xref:System.Windows.Controls.TextBox> veya kendisini kapsayan pencerenin boyutu genişletir.</span><span class="sxs-lookup"><span data-stu-id="f9f9b-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="f9f9b-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9f9b-108">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="f9f9b-109">TextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="f9f9b-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="f9f9b-110">RichTextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="f9f9b-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
