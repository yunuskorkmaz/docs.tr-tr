---
title: 'Nasıl yapılır: RichTextBox İçinde Özel Açılır Menü Konumlandırma'
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
ms.openlocfilehash: f9407f59c3daafd09fa5b84006f33ef2f3ebd31f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209430"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a><span data-ttu-id="e6d88-102">Nasıl yapılır: RichTextBox İçinde Özel Açılır Menü Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="e6d88-102">How to: Position a Custom Context Menu in a RichTextBox</span></span>
<span data-ttu-id="e6d88-103">Bu örnek için bir özel bağlam menüsü konumlandırma nasıl gösterir bir <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="e6d88-103">This example shows how to position a custom context menu for a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="e6d88-104">Özel bağlam menüsü için uyguladığınızda bir **RichTextBox**, bağlam menüsünü yerleşimini işlenmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e6d88-104">When you implement a custom context menu for a **RichTextBox**, you are responsible for handling the placement of the context menu.</span></span>  <span data-ttu-id="e6d88-105">Varsayılan olarak, merkezde özel bağlam menüsü açıldığında **RichTextBox**.</span><span class="sxs-lookup"><span data-stu-id="e6d88-105">By default, a custom context menu is opened at the center of the **RichTextBox**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6d88-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6d88-106">Example</span></span>  
 <span data-ttu-id="e6d88-107">Varsayılan yerleştirme davranışı geçersiz kılmak için için bir dinleyici eklemek <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> olay.</span><span class="sxs-lookup"><span data-stu-id="e6d88-107">To override the default placement behavior, add a listener for the <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event.</span></span>  <span data-ttu-id="e6d88-108">Aşağıdaki örnekte, program aracılığıyla bunun nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e6d88-108">The following example shows how to do this programmatically.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a><span data-ttu-id="e6d88-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e6d88-109">Example</span></span>  
 <span data-ttu-id="e6d88-110">Aşağıdaki örnek, karşılık gelen bir uygulamasını gösterir <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> olay dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e6d88-110">The following example shows an implementation the corresponding <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event listener.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="e6d88-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6d88-111">See also</span></span>

- [<span data-ttu-id="e6d88-112">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e6d88-112">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="e6d88-113">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e6d88-113">TextBox Overview</span></span>](textbox-overview.md)
