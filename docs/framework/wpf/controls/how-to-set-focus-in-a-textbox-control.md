---
title: "Nasıl yapılır: TextBox Denetiminde Odak Ayarlama"
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
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a2c25f9dbc05ac9d5c14eb794236613b49f8240e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-focus-in-a-textbox-control"></a><span data-ttu-id="19b47-102">Nasıl yapılır: TextBox Denetiminde Odak Ayarlama</span><span class="sxs-lookup"><span data-stu-id="19b47-102">How to: Set Focus in a TextBox Control</span></span>
<span data-ttu-id="19b47-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.UIElement.Focus%2A> odak ayarlamak için yöntemi bir <xref:System.Windows.Controls.TextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="19b47-103">This example shows how to use the <xref:System.Windows.UIElement.Focus%2A> method to set focus on a <xref:System.Windows.Controls.TextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19b47-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="19b47-104">Example</span></span>  
 <span data-ttu-id="19b47-105">Aşağıdaki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnek açıklar basit bir <xref:System.Windows.Controls.TextBox> adlı Denetim *tbFocusMe*</span><span class="sxs-lookup"><span data-stu-id="19b47-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] example describes a simple <xref:System.Windows.Controls.TextBox> control named *tbFocusMe*</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a><span data-ttu-id="19b47-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="19b47-106">Example</span></span>  
 <span data-ttu-id="19b47-107">Aşağıdaki örnek çağrıları <xref:System.Windows.UIElement.Focus%2A> odak ayarlamak için yöntemi <xref:System.Windows.Controls.TextBox> adlı Denetim *tbFocusMe*.</span><span class="sxs-lookup"><span data-stu-id="19b47-107">The following example calls the <xref:System.Windows.UIElement.Focus%2A> method to set the focus on the <xref:System.Windows.Controls.TextBox> control with the Name *tbFocusMe*.</span></span>  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a><span data-ttu-id="19b47-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19b47-108">See Also</span></span>  
 <xref:System.Windows.UIElement.Focusable%2A>  
 <xref:System.Windows.UIElement.IsFocused%2A>  
 [<span data-ttu-id="19b47-109">TextBox genel bakış</span><span class="sxs-lookup"><span data-stu-id="19b47-109">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="19b47-110">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="19b47-110">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
