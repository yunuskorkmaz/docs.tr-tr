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
ms.workload: dotnet
ms.openlocfilehash: 4651953ec8ae6373b9a6946b31f96213bec570cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-position-a-custom-context-menu-in-a-richtextbox"></a>Nasıl yapılır: RichTextBox İçinde Özel Bağlam Menüsü Konumlandırma
Bu örnek için özel bağlam menüsü konumlandırma gösterilmektedir bir <xref:System.Windows.Controls.RichTextBox>.  
  
 Uygulamanız için özel bağlam menüsü ne zaman bir **RichTextBox**, bağlam menüsü yerleşimini işlenmesinden sorumludur.  Varsayılan olarak merkezinde özel bağlam menüsü açılır **RichTextBox**.  
  
## <a name="example"></a>Örnek  
 Varsayılan yerleştirme davranışını geçersiz kılmak için bir dinleyici için ekleme <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> olay.  Aşağıdaki örnekte bu programlı olarak nasıl yapılacağını gösterir.  
  
 [!code-csharp[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_addlistener)]
 [!code-vb[RichTextBox_ContextMenu#_AddListener](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_addlistener)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, karşılık gelen bir uygulama gösterir <xref:System.Windows.FrameworkContentElement.ContextMenuOpening> olay dinleyicisi.  
  
 [!code-csharp[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_ContextMenu/CSharp/app.xaml.cs#_listenerbody)]
 [!code-vb[RichTextBox_ContextMenu#_ListenerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBox_ContextMenu/VisualBasic/app.xaml.vb#_listenerbody)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [RichTextBox Genel Bakış](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [TextBox Genel Bakış](../../../../docs/framework/wpf/controls/textbox-overview.md)
