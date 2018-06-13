---
title: 'Nasıl yapılır: Çok Satırlı TextBox Denetimi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 9f4c9e637b686c82b4ec8a4a5d6d3a78d46f97c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553293"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="c5fac-102">Nasıl yapılır: Çok Satırlı TextBox Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c5fac-102">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="c5fac-103">Bu örnek nasıl kullanılacağını gösterir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlamak için bir <xref:System.Windows.Controls.TextBox> birkaç satırlık metin uyum sağlayacak şekilde otomatik olarak genişletecek denetim.</span><span class="sxs-lookup"><span data-stu-id="c5fac-103">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5fac-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c5fac-104">Example</span></span>  
 <span data-ttu-id="c5fac-105">Ayarlama <xref:System.Windows.Controls.TextBox.TextWrapping%2A> özniteliğini **sarmalamak** yeni bir sarmalamak girilen metin neden olacak ne zaman satır köşesine <xref:System.Windows.Controls.TextBox> denetim ulaşıldığında, otomatik olarak genişleterek <xref:System.Windows.Controls.TextBox> yeni bir satır için oda eklenecek denetim gerekli.</span><span class="sxs-lookup"><span data-stu-id="c5fac-105">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="c5fac-106">Ayarlama <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> özniteliğini **true** RETURN tuşuna basıldığında otomatik olarak bir kez yeniden genişletme eklenecek yeni bir satır neden <xref:System.Windows.Controls.TextBox> gerekiyorsa, yeni bir satır için oda eklenecek.</span><span class="sxs-lookup"><span data-stu-id="c5fac-106">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="c5fac-107"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Özniteliği için bir kaydırma çubuğunun ekler <xref:System.Windows.Controls.TextBox>, böylece içeriğini <xref:System.Windows.Controls.TextBox> değilse kaydırılabileceğini <xref:System.Windows.Controls.TextBox> çerçeve ya da onu pencere boyutunu genişletir.</span><span class="sxs-lookup"><span data-stu-id="c5fac-107">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="c5fac-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5fac-108">See Also</span></span>  
 <xref:System.Windows.TextWrapping>  
 [<span data-ttu-id="c5fac-109">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c5fac-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="c5fac-110">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c5fac-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
