---
title: "Nasıl yapılır: ListView İçindeki Seçili Öğelere Stil Eklemek için Tetikleyicileri Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 1e2bdce0-afe8-4507-9b18-f33de43de25a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f8965ee524d6a5cb03a54ac07d8889ff9801440
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-triggers-to-style-selected-items-in-a-listview"></a><span data-ttu-id="7e38e-102">Nasıl yapılır: ListView İçindeki Seçili Öğelere Stil Eklemek için Tetikleyicileri Kullanma</span><span class="sxs-lookup"><span data-stu-id="7e38e-102">How to: Use Triggers to Style Selected Items in a ListView</span></span>
<span data-ttu-id="7e38e-103">Bu örnek nasıl tanımlanacağı gösterilmektedir <xref:System.Windows.Style.Triggers%2A> için bir <xref:System.Windows.Controls.ListViewItem> denetim için bir özellik değeri, bir <xref:System.Windows.Controls.ListViewItem> değişiklikleri, <xref:System.Windows.Style> , <xref:System.Windows.Controls.ListViewItem> yanıt değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="7e38e-103">This example shows how to define <xref:System.Windows.Style.Triggers%2A> for a <xref:System.Windows.Controls.ListViewItem> control so that when a property value of a <xref:System.Windows.Controls.ListViewItem> changes, the <xref:System.Windows.Style> of the <xref:System.Windows.Controls.ListViewItem> changes in response.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e38e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7e38e-104">Example</span></span>  
 <span data-ttu-id="7e38e-105">İsterseniz <xref:System.Windows.Style> , bir <xref:System.Windows.Controls.ListViewItem> özelliği değişikliklere yanıt değiştirmek için tanımlamak <xref:System.Windows.Style.Triggers%2A> için <xref:System.Windows.Style> değiştirin.</span><span class="sxs-lookup"><span data-stu-id="7e38e-105">If you want the <xref:System.Windows.Style> of a <xref:System.Windows.Controls.ListViewItem> to change in response to property changes, define <xref:System.Windows.Style.Triggers%2A> for the <xref:System.Windows.Style> change.</span></span>  
  
 <span data-ttu-id="7e38e-106">Aşağıdaki örnek tanımlar bir <xref:System.Windows.Trigger> ayarlayan <xref:System.Windows.Controls.Control.Foreground%2A> özelliğine <xref:System.Windows.Media.Brushes.Blue%2A> ve değişiklikleri <xref:System.Windows.FrameworkElement.Cursor%2A> görüntülemek için bir <xref:System.Windows.Input.CursorType.Hand> zaman <xref:System.Windows.UIElement.IsMouseOver%2A> özelliği değişiklikler `true`.</span><span class="sxs-lookup"><span data-stu-id="7e38e-106">The following example defines a <xref:System.Windows.Trigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property to <xref:System.Windows.Media.Brushes.Blue%2A> and changes the <xref:System.Windows.FrameworkElement.Cursor%2A> to display a <xref:System.Windows.Input.CursorType.Hand> when the <xref:System.Windows.UIElement.IsMouseOver%2A> property changes to `true`.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#Trigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#trigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
 <span data-ttu-id="7e38e-107">Aşağıdaki örnek tanımlayan bir <xref:System.Windows.MultiTrigger> ayarlayan <xref:System.Windows.Controls.Control.Foreground%2A> özelliği bir <xref:System.Windows.Controls.ListViewItem> için <xref:System.Windows.Media.Brushes.Yellow%2A> zaman <xref:System.Windows.Controls.ListViewItem> seçili öğe ve klavye odağı olan.</span><span class="sxs-lookup"><span data-stu-id="7e38e-107">The following example defines a <xref:System.Windows.MultiTrigger> that sets the <xref:System.Windows.Controls.Control.Foreground%2A> property of a <xref:System.Windows.Controls.ListViewItem> to <xref:System.Windows.Media.Brushes.Yellow%2A> when the <xref:System.Windows.Controls.ListViewItem> is the selected item and has keyboard focus.</span></span>  
  
 [!code-xaml[ListViewChkBox#ListViewItemTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersstart)]  
[!code-xaml[ListViewChkBox#MultiTrigger](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#multitrigger)]  
[!code-xaml[ListViewChkBox#ListViewItemTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewChkBox/CS/window1.xaml#listviewitemtriggersend)]  
  
## <a name="see-also"></a><span data-ttu-id="7e38e-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7e38e-108">See Also</span></span>  
 <xref:System.Windows.Controls.Control>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [<span data-ttu-id="7e38e-109">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="7e38e-109">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="7e38e-110">ListView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7e38e-110">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="7e38e-111">GridView Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7e38e-111">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
