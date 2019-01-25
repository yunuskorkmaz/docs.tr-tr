---
title: 'Nasıl yapılır: RichTextBox İçinde Özel Bağlam Menüsü Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
ms.openlocfilehash: 1f6e7255286d065eb26773d524a3147801933406
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727904"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a><span data-ttu-id="51aea-102">Nasıl yapılır: RichTextBox İçinde Özel Bağlam Menüsü Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="51aea-102">How to: Position a Custom Context Menu in a RichTextBox</span></span>
<span data-ttu-id="51aea-103">Bu örnek için bir özel bağlam menüsü konumlandırma nasıl gösterir bir <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="51aea-103">This example shows how to position a custom context menu for a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="51aea-104">Özel bağlam menüsü için uyguladığınızda bir **RichTextBox**, bağlam menüsünü yerleşimini işlenmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="51aea-104">When you implement a custom context menu for a **RichTextBox**, you are responsible for handling the placement of the context menu.</span></span>  <span data-ttu-id="51aea-105">Varsayılan olarak, merkezde özel bağlam menüsü açıldığında **RichTextBox**.</span><span class="sxs-lookup"><span data-stu-id="51aea-105">By default, a custom context menu is opened at the center of the **RichTextBox**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51aea-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="51aea-106">Example</span></span>  
 <span data-ttu-id="51aea-107">Varsayılan yerleştirme davranışı geçersiz kılmak için için bir dinleyici eklemek <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> olay.</span><span class="sxs-lookup"><span data-stu-id="51aea-107">To override the default placement behavior, add a listener for the <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event.</span></span>  <span data-ttu-id="51aea-108">Aşağıdaki örnekte, program aracılığıyla bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="51aea-108">The following example shows how to do this programmatically.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a><span data-ttu-id="51aea-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="51aea-109">Example</span></span>  
 <span data-ttu-id="51aea-110">Aşağıdaki örnek, karşılık gelen bir uygulamasını gösterir <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> olay dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="51aea-110">The following example shows an implementation the corresponding <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event listener.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="51aea-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51aea-111">See also</span></span>
- [<span data-ttu-id="51aea-112">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="51aea-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
- [<span data-ttu-id="51aea-113">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="51aea-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
