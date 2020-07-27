---
title: 'Nasıl yapılır: TextBox Denetiminde Odak Ayarlama'
description: Odak yönteminin bir Windows Presentation Foundation TextBox denetimine odaklanmak için nasıl kullanılacağını öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: e107c22a3c5b701e02cbc8506d10fa35ee15c79d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168054"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a><span data-ttu-id="88f0a-103">Nasıl yapılır: TextBox Denetiminde Odak Ayarlama</span><span class="sxs-lookup"><span data-stu-id="88f0a-103">How to: Set Focus in a TextBox Control</span></span>
<span data-ttu-id="88f0a-104">Bu örnek, <xref:System.Windows.UIElement.Focus%2A> bir denetim üzerinde odağı ayarlamak için yönteminin nasıl kullanılacağını gösterir <xref:System.Windows.Controls.TextBox> .</span><span class="sxs-lookup"><span data-stu-id="88f0a-104">This example shows how to use the <xref:System.Windows.UIElement.Focus%2A> method to set focus on a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88f0a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="88f0a-105">Example</span></span>  
 <span data-ttu-id="88f0a-106">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekte, <xref:System.Windows.Controls.TextBox> *tbFocusMe* adlı basit bir denetim açıklanmaktadır</span><span class="sxs-lookup"><span data-stu-id="88f0a-106">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example describes a simple <xref:System.Windows.Controls.TextBox> control named *tbFocusMe*</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a><span data-ttu-id="88f0a-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="88f0a-107">Example</span></span>  
 <span data-ttu-id="88f0a-108">Aşağıdaki örnek, <xref:System.Windows.UIElement.Focus%2A> <xref:System.Windows.Controls.TextBox> *tbFocusMe*adlı denetimin üzerindeki odağı ayarlamak için yöntemini çağırır.</span><span class="sxs-lookup"><span data-stu-id="88f0a-108">The following example calls the <xref:System.Windows.UIElement.Focus%2A> method to set the focus on the <xref:System.Windows.Controls.TextBox> control with the Name *tbFocusMe*.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a><span data-ttu-id="88f0a-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88f0a-109">See also</span></span>

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [<span data-ttu-id="88f0a-110">TextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="88f0a-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="88f0a-111">RichTextBox Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="88f0a-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
