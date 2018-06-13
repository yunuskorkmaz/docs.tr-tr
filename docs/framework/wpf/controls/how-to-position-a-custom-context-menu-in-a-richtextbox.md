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
ms.openlocfilehash: bde28cdb87bdaef3198d1efd3059fed3d0ae0ce2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553864"
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a><span data-ttu-id="e1041-102">Nasıl yapılır: RichTextBox İçinde Özel Bağlam Menüsü Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="e1041-102">How to: Position a Custom Context Menu in a RichTextBox</span></span>
<span data-ttu-id="e1041-103">Bu örnek için özel bağlam menüsü konumlandırma gösterilmektedir bir <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="e1041-103">This example shows how to position a custom context menu for a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="e1041-104">Uygulamanız için özel bağlam menüsü ne zaman bir **RichTextBox**, bağlam menüsü yerleşimini işlenmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="e1041-104">When you implement a custom context menu for a **RichTextBox**, you are responsible for handling the placement of the context menu.</span></span>  <span data-ttu-id="e1041-105">Varsayılan olarak merkezinde özel bağlam menüsü açılır **RichTextBox**.</span><span class="sxs-lookup"><span data-stu-id="e1041-105">By default, a custom context menu is opened at the center of the **RichTextBox**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1041-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1041-106">Example</span></span>  
 <span data-ttu-id="e1041-107">Varsayılan yerleştirme davranışını geçersiz kılmak için bir dinleyici için ekleme <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> olay.</span><span class="sxs-lookup"><span data-stu-id="e1041-107">To override the default placement behavior, add a listener for the <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event.</span></span>  <span data-ttu-id="e1041-108">Aşağıdaki örnekte bu programlı olarak nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e1041-108">The following example shows how to do this programmatically.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a><span data-ttu-id="e1041-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1041-109">Example</span></span>  
 <span data-ttu-id="e1041-110">Aşağıdaki örnek, karşılık gelen bir uygulama gösterir <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> olay dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="e1041-110">The following example shows an implementation the corresponding <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event listener.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="e1041-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e1041-111">See Also</span></span>  
 [<span data-ttu-id="e1041-112">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e1041-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="e1041-113">TextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e1041-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
