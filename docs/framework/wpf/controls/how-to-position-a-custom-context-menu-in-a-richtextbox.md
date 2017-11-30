---
title: "Nasıl yapılır: RichTextBox İçinde Özel Bağlam Menüsü Konumlandırma"
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
- custom context menus [WPF], positioning
- positioning custom context menus [WPF]
- RichTextBox control [WPF], positioning custom context menus
- context menus [WPF], positioning
ms.assetid: bf77c930-a546-4573-9a56-9af345ba189a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1c0a4fd8d2df15dcca2d9d1751f3089922d9a5ad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a><span data-ttu-id="45d37-102">Nasıl yapılır: RichTextBox İçinde Özel Bağlam Menüsü Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="45d37-102">How to: Position a Custom Context Menu in a RichTextBox</span></span>
<span data-ttu-id="45d37-103">Bu örnek için özel bağlam menüsü konumlandırma gösterilmektedir bir <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="45d37-103">This example shows how to position a custom context menu for a <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="45d37-104">Uygulamanız için özel bağlam menüsü ne zaman bir **RichTextBox**, bağlam menüsü yerleşimini işlenmesinden sorumludur.</span><span class="sxs-lookup"><span data-stu-id="45d37-104">When you implement a custom context menu for a **RichTextBox**, you are responsible for handling the placement of the context menu.</span></span>  <span data-ttu-id="45d37-105">Varsayılan olarak merkezinde özel bağlam menüsü açılır **RichTextBox**.</span><span class="sxs-lookup"><span data-stu-id="45d37-105">By default, a custom context menu is opened at the center of the **RichTextBox**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45d37-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="45d37-106">Example</span></span>  
 <span data-ttu-id="45d37-107">Varsayılan yerleştirme davranışını geçersiz kılmak için bir dinleyici için ekleme <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> olay.</span><span class="sxs-lookup"><span data-stu-id="45d37-107">To override the default placement behavior, add a listener for the <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event.</span></span>  <span data-ttu-id="45d37-108">Aşağıdaki örnekte bu programlı olarak nasıl yapılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="45d37-108">The following example shows how to do this programmatically.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a><span data-ttu-id="45d37-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="45d37-109">Example</span></span>  
 <span data-ttu-id="45d37-110">Aşağıdaki örnek, karşılık gelen bir uygulama gösterir <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> olay dinleyicisi.</span><span class="sxs-lookup"><span data-stu-id="45d37-110">The following example shows an implementation the corresponding <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> event listener.</span></span>  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="45d37-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45d37-111">See Also</span></span>  
 [<span data-ttu-id="45d37-112">RichTextBox Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="45d37-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="45d37-113">TextBox genel bakış</span><span class="sxs-lookup"><span data-stu-id="45d37-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
